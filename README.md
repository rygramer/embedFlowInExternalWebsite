# How to Embed a Flow in an External Website
In order to embed a Flow in an external website (like Wordpress), you have to:
1. create an Aura Component;
2. create an Aura App; and
3. add a few lines of code to your website.

You can use this sfdx project as a base configuration, you'll just need to make one small to the code to make it yours. In the `embedFlowInExternalWebsite.cmp` file of the Aura component, add YOUR_FLOW_API_NAME.
```javascript
({
    init : function (component) {
        var flow = component.find("flowData");
        flow.startFlow("YOUR_FLOW_API_NAME");
    }
})
```

Here's the code for your to copy and paste into your website. Be sure to replace YOUR-SALESFORCE-SITE-URL; it should be something like `https://xxx.na163.force.com/`.s
```javascript
<script src="https://YOUR-SALESFORCE-SITE-URL.com/lightning/lightning.out.js"></script>

<div id="lightningLocator"></div>

<script>
    $Lightning.use("c:embedFlowInExternalWebsiteApp",
        function() {
            $Lightning.createComponent(
                "c:embedFlowInExternalWebsite",
                { },                  
                "lightningLocator",   
                function(cmp) {}
            );
        },
        'https://YOUR-SALESFORCE-SITE-URL.com'  // Site endpoint
    );
</script>
```