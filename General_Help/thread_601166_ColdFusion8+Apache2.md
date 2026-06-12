---
title: "ColdFusion8+Apache2"
date: 2007-11-02
forum: General Help
---

### Post by hebetude on 2007-11-02
I installed Coldfusion and it went surprisingly smoothly.  The administrator page loads normally, but I can't get any coldfusion code to load in firefox.

```
<cfsavecontent variable="changeTheme">
    _root.ThemeColor.setStyle("themeColor",_root.ThemeColor.selectedItem.data)&#894;
</cfsavecontent>
<cfform format="flash" skin="haloblue">
    <cfselect name="ThemeColor" width="100" onChange="#changeTheme#">
        <option value="haloblue">Blue</option>
        <option value="halogreen">Green</option>
        <option value="haloorange">Orange</option>
        <option value="halosilver">Silver</option>
    </cfselect>
    <cfinput type="button" name="mybtn" value="I'm haloblue">
</cfform>
```

I put this on my server, hit the page through apache and nothing shows up.  The view source shows a bunch of javascript, but all I see is a white page.  I've uninstalled my adblocker, but can't figure out the problem here.

Here's the javascript:
```

<script type="text/javascript" src="/CFIDE/scripts/cfform.js"></script>
<script type="text/javascript" src="/CFIDE/scripts/masks.js"></script>

<script type="text/javascript" charset='utf-8' src='/CFIDE/scripts/cfformhistory.js'></script>
<noscript>
    <embed pluginspage='http://www.macromedia.com/go/getflashplayer' id='CFForm_1' src='/dev/549998822.mxml.cfswf' width='100%' height='100%' wMode='Window' flashVars='%5F%5FCFForm%5F1%5Fcacheid=03A60999%2DA943%2D0D85%2DE2E48698DBD635AE' ></embed>
</noscript>
<script type="text/javascript" charset='utf-8'>
    document.write("<embed pluginspage='http://www.macromedia.com/go/getflashplayer' ");
    document.write("   id='CFForm_1' ");
    document.write("   src='/dev/549998822.mxml.cfswf' ");
    document.write("   width='100%' ");
    document.write("   height='100%' ");
    document.write("   wMode='Window' ");
    document.write("   flashVars='historyUrl=%2FCFIDE%2Fscriptscfformhistory%2Ecfm%3F&lconid=" + lc_id +"&%5F%5FCFForm%5F1%5Fcacheid=03A60999%2DA943%2D0D85%2DE2E48698DBD635AE' ></embed>");
</script>
<script type="text/javascript" charset='utf-8'>
    document.write("<br><iframe src='/CFIDE/scripts/cfformhistory.cfm' name='_history' frameborder='0' scrolling='no' width='22' height='0'></iframe></br> ");

```

I moved the file to document root, but to no avail firefox just shows a blank screen.  Do cfForms not work in ubuntu/apache?  
</script>

---

