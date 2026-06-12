---
title: "widescreen monitor: web pages constricted to centre with blank spaces on either side"
date: 2020-05-26
forum: General Help
---

### Post by Kanfused on 2020-05-26
I have a 22inch LG 22MK430H monitor bought recently. This is a full hd monitor used at 1920x1080 @75hz. The problem is that many websites are not displayed correctly covering whole screen area. Most pages are displayed centered or in the middle with blank spaces on the left and right side. Is there any fix to this. The most annoying problem is web search results from Google displayed aligned on to the left side corner with almost 1/3rd of the screen remains unused. Zooming the browser doesn't fix this.  The problem is present in both Firefox and Chrome. 
EDIT: Zoom in with the browser is not a solution to this problem.
See the screenshots:
[ATTACH=CONFIG]286023[/ATTACH][ATTACH=CONFIG]286024[/ATTACH]

---

### Post by Holger_Gehrke on 2020-05-26
Not much you can do about it. Most modern websites follow the design idea of "mobile first" meaning they are designed to be usable and look good on a smart phone in portrait orientation. Look and usability on big displays in landscape orientation is at best secondary. You could try overriding the CSS the sites use with a userContent.css in the 'chrome'-directory in your Firefox profile directory. And no, this has nothing to do with the browser named chrome; 'chrome' as a term in browsers used to refer to all purely cosmetic elements and was used in that way long before Google published their browser. An alternative to this is to use the Firefox extension Stylish which allows you to set up your own styles for every web site.

Holger

---

### Post by CelticWarrior on 2020-05-26
Just use zoom:
CTRL + + to increase;
CTRL + - to decrease.

---

### Post by sdsurfer on 2020-05-26
Right click page
Select "Inspect Element" in FireFox or similar in other browsers, Chrome is "Inspect"
This will show you the HTML and associated  CSS. In one of the outer elements beginning with the body element, click it in the inspector panel and look at the CSS associated with it.

```

<! doctype html>
 <head>
 </head>
<body> <!--- Body container -->
  <div id="page-container">
    <header id="top-header">
    blah blah
    </header>
    <div id="page-content">
     blah blah
    </div>
   </div>
  </body>
</html>

```

You will very likely find a max-width property somewhere, like max-width: 1024px. In most inspectors there are checkboxes by the property, in the CSS tab you can uncheck them and see the effect on the page (goes away when you reload.)

The reason for this: imagine if the page did expand to the full width of your monitor. Text lines would be very wide and it becomes difficult to follow to the next line. It is a consideration of legibility.

---

### Post by Kanfused on 2020-05-26
Looks like better luck with some extensions. I remember using stylish, greasemonkey etc to fix this issue many years back.  There used to be an extension that fixed the Google search results to fill the horizontal area. Thank you for the replies.

---

### Post by Autodave on 2020-05-26
Did you try using the CTRL key and the + sign?  I am on the same size monitor with no issues.

If that does not work, what video card are you using?  What driver, if any, are you using and where did you get it from?  How is the monitor hooked to the PC: VGA, HDMI, DVI?

---

### Post by Kanfused on 2020-05-27
Zoom in & out are no solution. I think stylish and such extensions may be helpful. But, sadly I do not know CSS.

---

