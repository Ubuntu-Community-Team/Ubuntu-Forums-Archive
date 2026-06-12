---
title: "Firefox 91 - GUI changed again - whitespace in menus."
date: 2021-08-12
forum: General Help
---

### Post by ajgreeny on 2021-08-12
I have just upgraded all packages on my Xubuntu 20.04 and find that firefox 91 has again made unnecessary and as far as I'm concerned very annoying changes to the GUI and has re-introduced huge amounts of wasted whitespace in all menus, eg Bookmarks, Application Menu (from the hamburger icon top right) meaning that some menus, Bookmarks in particular need a lot of scrolling to see everything.
I had previously managed to get rid of that space by disabling proton in the **about:config** page but that is no longer effective.

What is the point of all this white space?
Touchscreens may need it but not a package for a more normal PC using a mouse or touchpad surely!

I know there has been a lot of discussion about firefox GUI changes since FF 89 appeared but this most recent change seems to be more permanent and I am not sure how effective changes made on the userChrome.css file mentioned in these threads is now working as it did.
See threads
[https://ubuntuforums.org/showthread.php?t=2463096](https://ubuntuforums.org/showthread.php?t=2463096)
[https://ubuntuforums.org/showthread.php?t=2463077](https://ubuntuforums.org/showthread.php?t=2463077)

---

### Post by sudodus on 2021-08-12
Please show with screenshots how the whitespace has increased in Firefox 91. I use it too, but am not sure what you mean when I compare my current Firefox with yours screenshots from the two links.

I think that the height of the items have increased. so that the vertical spacing has increased. Is there also some other change, that is wasting space?

---

### Post by monkeybrain20122 on 2021-08-12
It looks the same to me before the upgrade. Do you have a screenshot?

---

### Post by ajgreeny on 2021-08-12
I don't have a screenshot from FF-90 of the menu from the hamburger icon top right or Bookmarks menu from the toolbar icon that I use but I have just taken sceenshots of the wasted space caused by the whitespace in menus in FF-91.

I agree that the height of the toolbars has also been increased a bit wasting more screenspace for no good reason, and I've just noticed that I have lost the FF icon top left in the tabs toolbar; not too important but I did like it and my userChrome.css is still set to show it as it was in FF-90.

All relatively minor things in some ways, but still annoying!

---

### Post by Holger_Gehrke on 2021-08-12
To regain the lost vertical space, you can set 'browser.compactmode.show' to true in 'about:config' and then go to 'customize toolbars' (retranslated from German 'Symbolleisten anpassen') and choose 'Density' -> 'Compact (unsupported)' on the bottom of the window.

Reducing the space between menu items is possible by including this bit in your userChrome.css:
```

subview-subheader, panelview .toolbarbutton-1, .subviewbutton, .widget-overflow-list .toolbarbutton-1 {

    margin: 2px 2px !important;
    min-height: 16px !important;
    padding: 2px 2px !important;
}

```
You might want to play around with the values for margin and padding to strike a balance between density and readability.

And to get the tabs back to looking like tabs instead of free floating buttons, this bit of css:
```

.tab-background{
     border-radius: 0px 0px !important;
     margin-bottom: 0px !important;
}

```
If you like rounded corners on the active tab, play with the values for border-radius.

Holger

---

### Post by ajgreeny on 2021-08-13
Holger, I tried that entry to change the whitespace in menus but it has made no difference at all.

I have also totally removed the userChrome.css file which did not change anything at all in the GUI and then as a test, made a lot of edits, none of which changed anything.
I am now beginning to consider the possibility that the userChrome.css configuration file has been completely disabled and has no effect any more.
Any thoughts or ideas about that?

[COLOR="#FF0000"]EDIT:[/COLOR]
Well I have no idea how this happened unless it was the move the FF-91 but I found that the userChrome.css was indeed disabled and needed enabling again by toggling the about:config entry of ***toolkit.legacyUserProfileCustomizations.stylesheets*** from false to true.
This has brought back the GUI that I had in FF-89 after making many edits to the userChrome.css file.

---

### Post by mikewhatever on 2021-08-13
Actually, what Holder posted worked well here. It used to be more compact, but floating tabs are gone.

---

### Post by monkeybrain20122 on 2021-08-13
> **ajgreeny said:**
> I don't have a screenshot from FF-90 of the menu from the hamburger icon top right or Bookmarks menu from the toolbar icon that I use but I have just taken sceenshots of the wasted space caused by the whitespace in menus in FF-91.

I agree that the height of the toolbars has also been increased a bit wasting more screenspace for no good reason, and I've just noticed that I have lost the FF icon top left in the tabs toolbar; not too important but I did like it and my userChrome.css is still set to show it as it was in FF-90.

All relatively minor things in some ways, but still annoying!

I see, since I don't use the menu and bookmark bars I don't see any difference.

---

### Post by ajgreeny on 2021-08-14
I don't use the menubar either but I do have the Show Bookmarks icon in my toolbar which opens a bookmarks menu, now stretched out so much that it doesn't fit my screen.

As I said, it's not a major problem, just annoying!

---

### Post by ajgreeny on 2021-08-17
I have just looked at the information at [https://forums.linuxmint.com/viewtopic.php?p=2053855#p2053855](https://forums.linuxmint.com/viewtopic.php?p=2053855#p2053855) which I found at the linuxmint forum. This offers another method, now named Lepton, of dealing with this GUI problem in FF and it does seem to get rid of the whitespace in menus, my main worry at the moment.
However it does not give me the coloured icons in the toolbar that make life a lot quicker for me; I dislike monochrome, boring icons which always need a closer loo, to see which is which.

---

### Post by &amp;KyT$0P# on 2021-08-17
> **ajgreeny said:**
> However it does not give me the coloured icons in the toolbar that make life a lot quicker for me; 

Which icon do you want colored?

---

### Post by ajgreeny on 2021-08-17
All of them!

I've tried just about all the available options in the userChrome.css but can not get away from monochrome toolbar icons so far, but it's a huge css file (899KB) so I may have not searched well enough so far; too many other more important things to do!

---

### Post by Holger_Gehrke on 2021-08-17
The (built-in) browser tools allow you to select elements of the UI and get the CSS-rules that govern their look. Call them either from 'Extras' in the menu or hit 'ctrl-shift-alt-i'. For example the icon for the back-button has a rule
```

#back-button {
    list-style-image: url("chrome://browser/skin/back.svg");
}

```
overriding this should allow you to style the back-button any way you want ...

Holger

---

### Post by &amp;KyT$0P# on 2021-08-17
> **ajgreeny said:**
> I've tried just about all the available options in the userChrome.css but can not get away from monochrome toolbar icons so far, but it's a huge css file (899KB) so I may have not searched well enough so far; 

Wait, what?  That sounds more time consuming than just coming up with the code yourself.  It isn't hard once you know how. :)

Use Browser Toolbox to inspect the element so you can determine the best [CSS selector]("https://www.w3.org/TR/selectors-3/#selectors"): first ensure about:config > [FONT=Courier New]devtools.chrome.enabled[/FONT] and [FONT=Courier New]devtools.debugger.remote-enabled[/FONT] are both set to [FONT=Courier New]true[/FONT] , then do Ctrl-Alt-Shift-I, click OK on the dialog and the devtools should be up.  Click Inspector, then click the arrow icon in the top left so you can click on the element (in this case, toolbar icon) you want to inspect.  Once you've inspected the element and decided on a CSS selector, then try various different methods of re-styling images until you find one that works.

For example, to restyle Reload button, Stop button, and Back/Forward buttons, does the following CSS work? (adjust the colors to suit your preferences) -
```
#reload-button {
  fill: #0000ff !important;
}
#stop-button {
  fill: #ff0000 !important;
}
#back-button, #forward-button {
  fill: #009900 !important;
}
```

---

