---
title: "Firefox 89 downgrade to 88.0.2"
date: 2021-06-03
forum: General Help
---

### Post by matrooswolf on 2021-06-03
Hi,
I really don't like the new Firefox 89 and it broke my css (to have tabs at the bottom). I tried a lot already to get the tabs back at the bottom (other css), but nothing works.

So, is it possible to safely downgrade Firefox to 88.0.1 again which worked perfect for me (without breaking anything and keeping my settings)?

All help is welcome!

---

### Post by Impavidus on 2021-06-03
No. Downgrading packages is usually hard, simply because the old versions get removed from the repositories (except kernel upgrades). It may still be in your cache. Furthermore, Firefox 88 won't get any more security upgrades, which are somewhat important for a web browser.

---

### Post by monkeybrain20122 on 2021-06-03
You can download a binary from Mozilla and run it locally.

---

### Post by ActionParsnip on 2021-06-03
Uninstall the current version and you can then reinstall with the older version.

---

### Post by Dennis N on 2021-06-03
All packaging types for Firefox have automatic upgrading by default - so if you downgrade, it will just just upgrade again. You can block upgrades to the apt version and maybe the Mozilla direct version, but as mentioned, the web browser is especially important to keep up to date for security, so you should adapt to the changes. That's progress, as they say.

---

### Post by matrooswolf on 2021-06-03
Hi everybody,

I understand the security issues, but usability is first on my list.

So, I would keep Firefox 89 is someone knows how to get my old layout back, which is simply: tabs under the address bar. Up until version 88 I had a css to do that, but I had to delete it as the new version messes up completely with the css. So, does anybody know how to do that? I see a lot of people complaining about that, but no viable solution.

It would be nice by the way if Mozilla had a switch in about:config to do that...

@ActionParsnip> Uninstall the current version and you can then reinstall with the older version.  Can you tell me how I would do that? 

Thanks!

---

### Post by ardouronerous on 2021-06-03
> **matrooswolf said:**
> Hi everybody,

I understand the security issues, but usability is first on my list.

So, I would keep Firefox 89 is someone knows how to get my old layout back, which is simply: tabs under the address bar. Up until version 88 I had a css to do that, but I had to delete it as the new version messes up completely with the css. So, does anybody know how to do that? I see a lot of people complaining about that, but no viable solution.

It would be nice by the way if Mozilla had a switch in about:config to do that...

@ActionParsnip Can you tell me how I would do that? 

Thanks!

See if setting *[FONT=arial]**browser.proton.enabled **[/FONT]*to** *[FONT=arial]false[/FONT]*** in *[FONT=arial]**about:config**[/FONT]* does anything.

---

### Post by ardouronerous on 2021-06-03
Also, check if ***[FONT=arial]toolkit.legacyUserProfileCustomizations.stylesheet[/FONT]s*** is set to ***[FONT=arial]true[/FONT]*** in ***[FONT=arial]about:config[/FONT]***. That maybe the reason why you're CSS has stopped working.

---

### Post by matrooswolf on 2021-06-03
> **ardouronerous said:**
> Also, check if ***[FONT=arial]toolkit.legacyUserProfileCustomizations.stylesheet[/FONT]s*** is set to ***[FONT=arial]true[/FONT]*** in ***[FONT=arial]about:config[/FONT]***. That maybe the reason why you're CSS has stopped working.

Hi,

I already disabled everything Proton, brings back the delimiters between the tabs, but doesn't do much more.

toolkit.legacyUserProfileCustomizations.stylesheet is set to true.

But with my old css (which worked fine up until 88.0.1) this is what I get: tabs go to the bottom of the screen, and only one tab is visible (see attachment)

I don't know css well enough to change it to get the tabs under the address bar. If anybody does, please let me know!

Thanks.

---

### Post by ardouronerous on 2021-06-03
> **matrooswolf said:**
> Hi,

I already disabled everything Proton, brings back the delimiters between the tabs, but doesn't do much more.

toolkit.legacyUserProfileCustomizations.stylesheet is set to true.

But with my old css (which worked fine up until 88.0.1) this is what I get: tabs go to the bottom of the screen, and only one tab is visible (see attachment)

I don't know css well enough to change it to get the tabs under the address bar. If anybody does, please let me know!

Thanks.

Sorry I couldn't be of anymore help, my experience in CSS is non-existent. I would suggest that you ask in [r/FirefoxCSS]("https://www.reddit.com/r/FirefoxCSS/").

---

### Post by CatKiller on 2021-06-03
> **matrooswolf said:**
> But with my old css (which worked fine up until 88.0.1) this is what I get: tabs go to the bottom of the screen, and only one tab is visible (see attachment)

I don't know css well enough to change it to get the tabs under the address bar. If anybody does, please let me know!

I also had exactly this problem, and I also don't know CSS. However, it seems [these people](http://forums.mozillazine.org/viewtopic.php?f=38&t=3075330) do.

I changed the part of my CSS that said

```
#TabsToolbar {
  -moz-box-ordinal-group: 1000 !important;
  display: block !important;
  position: absolute !important;
  bottom: 0 !important;
  width: 100vw !important;
}
```

to

```
*|*:root {
 --menubar-height: 36px;
 --tabbar-top: calc(var(--menubar-height) + var(--tab-min-height) + 0px); /*89+*/
}

#TabsToolbar {
display: block !important;
position: absolute !important;
top: var(--tabbar-top) !important;
width: 100vw !important;
}
```

and it works OK. Still looks a bit janky with a line through the tabs from the top of the content frame, but it's not completely broken like it was before.

---

### Post by Dennis N on 2021-06-03
A medium term solution might be to install the Firefox ESR version from Software. Choose the esr/stable version from the Source list on the Firefox page (see screenshot). It's the last one in the dropdown list. Right now its using Firefox 78

---

### Post by matrooswolf on 2021-06-03
> **ardouronerous said:**
> Sorry I couldn't be of anymore help, my experience in CSS is non-existent. I would suggest that you ask in [r/FirefoxCSS]("https://www.reddit.com/r/FirefoxCSS/").

Well, then your experience matches mine ;) But thank you for that suggestion. There is a working solution there. 

I replaced my old userChrome.ccs with the code from this post ```
https://www.reddit.com/r/FirefoxCSS/comments/nq2d0q/tabs_on_bottom_for_firefox_89/
``` et voilà, the world has been saved again!

Thank you!

---

### Post by ajgreeny on 2021-06-03
You may also find that there are changes you can make that are available from [https://github.com/Aris-t2/CustomCSSforFx/releases](https://github.com/Aris-t2/CustomCSSforFx/releases)

I used info from here in the past (4 years ago) and it made may GUI items a lot more acceptable to me.
I haven't yet had time to deal with the changes that have just appeared when I upgraded everything about 10 minutes ago but I'll be looking to see what's possible very soon.

---

### Post by matrooswolf on 2021-06-03
For those who are interested, this is the css I'm using```
 /* Source file https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/tabs_on_bottom.css made available under Mozilla Public License v. 2.0
See the above repository for updates as well as full license text. */

/* Modify to change window drag space width */
/*
Use tabs_on_bottom_menubar_on_top_patch.css if you
have menubar permanently enabled and want it on top
*/

/* IMPORTANT */
/*
Get window_control_placeholder_support.css
Window controls will be all wrong without it.
Additionally on Linux, you may need to get:
linux_gtk_window_control_patch.css
*/

:root{ --uc-titlebar-padding: 0px; }
@media (-moz-os-version: windows-win10){
:root[sizemode="maximized"][tabsintitlebar]{ --uc-titlebar-padding: 8px }
}
#toolbar-menubar[autohide="true"] > .titlebar-buttonbox-container,
#TabsToolbar > .titlebar-buttonbox-container{
position: fixed;
display: block;
top: var(--uc-titlebar-padding,0px);
right:0;
height: 40px;
}
/* Mac specific. You should set that font-smoothing pref to true if you are on any platform where window controls are on left */
@supports -moz-bool-pref("layout.css.osx-font-smoothing.enabled"){
:root{ --uc-titlebar-padding: 0px !important }
.titlebar-buttonbox-container{ left:0; right: unset !important; }
}

:root[uidensity="compact"] #TabsToolbar > .titlebar-buttonbox-container{ height: 32px }

#toolbar-menubar[inactive] > .titlebar-buttonbox-container{ opacity: 0 }

#navigator-toolbox{ padding-top: var(--uc-titlebar-padding,0px) !important; }

.titlebar-buttonbox-container > .titlebar-buttonbox{ height: 100%; }

#titlebar{
-moz-box-ordinal-group: 2;
-moz-appearance: none !important;
--tabs-navbar-shadow-size: 0px;
}

.titlebar-placeholder,
#TabsToolbar .titlebar-spacer{ display: none; }
/* Also hide the toolbox bottom border which isn't at bottom with this setup */
#navigator-toolbox::after{ display: none !important; }

@media (-moz-gtk-csd-close-button){ .titlebar-button{ -moz-box-orient: vertical } }

/* These exist only for compatibility with autohide-tabstoolbar.css */
toolbox#navigator-toolbox > toolbar#nav-bar.browser-toolbar{ animation: none; }
#navigator-toolbox:hover #TabsToolbar{ animation: slidein ease-out 48ms 1 }

/* Source file https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/tabs_on_bottom_menubar_on_top_patch.css made available under Mozilla Public License v. 2.0
See the above repository for updates as well as full license text. */

/* Menubar on top patch - use with tabs_on_bottom.css */
/* Only really useful if menubar is ALWAYS visible */

:root{ --uc-window-control-width: 0px !important }

#navigator-toolbox{ padding-top: calc(29px + var(--uc-titlebar-padding,0px)) !important }

#toolbar-menubar{
position: fixed;
display: flex;
top: var(--uc-titlebar-padding,0px);
height: 29px;
width: 100%;
overflow: hidden;
}

#toolbar-menubar > .titlebar-buttonbox-container{ height: 29px; order: 100; }

#toolbar-menubar > [flex]{ flex-grow: 100; }
#toolbar-menubar > spacer[flex]{
order: 99;
flex-grow: 1;
min-width: var(--uc-window-drag-space-width,20px);
}

#toolbar-menubar .titlebar-button{ padding: 2px 17px !important; }

#toolbar-menubar .toolbarbutton-1 { --toolbarbutton-inner-padding: 3px }

/* TABS: height */*|*:root { --tab-toolbar-navbar-overlap: 0px !important; --tab-min-height: 25px !important;
--tab-min-width: 80px !important;

#tabbrowser-tabs {
width: 100vw !important;
}
#main-window:not([chromehidden*="toolbar"]) #navigator-toolbox {padding-bottom: var(--tab-min-height) !important;}

.tab-background {
border-radius: 8px 8px 0px 0px !important; border-image: none !important;
}
.tab-line {
display: none;
}

.tab-close-button {
color: red!important;
} /* Source file https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/tabs_on_bottom.css made available under Mozilla Public License v. 2.0
See the above repository for updates as well as full license text. */

/* Modify to change window drag space width */
/*
Use tabs_on_bottom_menubar_on_top_patch.css if you
have menubar permanently enabled and want it on top
*/

/* IMPORTANT */
/*
Get window_control_placeholder_support.css
Window controls will be all wrong without it.
Additionally on Linux, you may need to get:
linux_gtk_window_control_patch.css
*/

:root{ --uc-titlebar-padding: 0px; }
@media (-moz-os-version: windows-win10){
:root[sizemode="maximized"][tabsintitlebar]{ --uc-titlebar-padding: 8px }
}
#toolbar-menubar[autohide="true"] > .titlebar-buttonbox-container,
#TabsToolbar > .titlebar-buttonbox-container{
position: fixed;
display: block;
top: var(--uc-titlebar-padding,0px);
right:0;
height: 40px;
}
/* Mac specific. You should set that font-smoothing pref to true if you are on any platform where window controls are on left */
@supports -moz-bool-pref("layout.css.osx-font-smoothing.enabled"){
:root{ --uc-titlebar-padding: 0px !important }
.titlebar-buttonbox-container{ left:0; right: unset !important; }
}

:root[uidensity="compact"] #TabsToolbar > .titlebar-buttonbox-container{ height: 32px }

#toolbar-menubar[inactive] > .titlebar-buttonbox-container{ opacity: 0 }

#navigator-toolbox{ padding-top: var(--uc-titlebar-padding,0px) !important; }

.titlebar-buttonbox-container > .titlebar-buttonbox{ height: 100%; }

#titlebar{
-moz-box-ordinal-group: 2;
-moz-appearance: none !important;
--tabs-navbar-shadow-size: 0px;
}

.titlebar-placeholder,
#TabsToolbar .titlebar-spacer{ display: none; }
/* Also hide the toolbox bottom border which isn't at bottom with this setup */
#navigator-toolbox::after{ display: none !important; }

@media (-moz-gtk-csd-close-button){ .titlebar-button{ -moz-box-orient: vertical } }

/* These exist only for compatibility with autohide-tabstoolbar.css */
toolbox#navigator-toolbox > toolbar#nav-bar.browser-toolbar{ animation: none; }
#navigator-toolbox:hover #TabsToolbar{ animation: slidein ease-out 48ms 1 }

/* Source file https://github.com/MrOtherGuy/firefox-csshacks/tree/master/chrome/tabs_on_bottom_menubar_on_top_patch.css made available under Mozilla Public License v. 2.0
See the above repository for updates as well as full license text. */

/* Menubar on top patch - use with tabs_on_bottom.css */
/* Only really useful if menubar is ALWAYS visible */

:root{ --uc-window-control-width: 0px !important }

#navigator-toolbox{ padding-top: calc(29px + var(--uc-titlebar-padding,0px)) !important }

#toolbar-menubar{
position: fixed;
display: flex;
top: var(--uc-titlebar-padding,0px);
height: 29px;
width: 100%;
overflow: hidden;
}

#toolbar-menubar > .titlebar-buttonbox-container{ height: 29px; order: 100; }

#toolbar-menubar > [flex]{ flex-grow: 100; }
#toolbar-menubar > spacer[flex]{
order: 99;
flex-grow: 1;
min-width: var(--uc-window-drag-space-width,20px);
}

#toolbar-menubar .titlebar-button{ padding: 2px 17px !important; }

#toolbar-menubar .toolbarbutton-1 { --toolbarbutton-inner-padding: 3px }

/* TABS: height */*|*:root { --tab-toolbar-navbar-overlap: 0px !important; --tab-min-height: 25px !important;
--tab-min-width: 80px !important;

#tabbrowser-tabs {
width: 100vw !important;
}
#main-window:not([chromehidden*="toolbar"]) #navigator-toolbox {padding-bottom: var(--tab-min-height) !important;}

.tab-background {
border-radius: 8px 8px 0px 0px !important; border-image: none !important;
}
.tab-line {
display: none;
}

.tab-close-button {
color: red!important;
}
```

---

### Post by ajgreeny on 2021-06-03
And I have now downloaded the custom css mentioned above in post ~14 and got FF89 looking just as I want it.

I like to keep the tabs at the top, above the addressbar, but remove the titlebar and menubar completely to save screenspace as much as possible. If I need the menubar Alt shows it temporarily as it always has.

The top part of my FF window, toolbars etc, now looks just as I wanted it, as shown in my screenshot.

PS:
The link for the particular custom.css that I downloaded is
[custom_css_for_fx_v3.2.1pre4.zip](custom_css_for_fx_v3.2.1pre4.zip)

Once extracted you can edit parts of the userChrome.css file as you wish, putting tabs above or below the addressbar, or even at the bottom of the window, I think, and can colourise icons as I have them.
Most of the text of the file is self-explanatory, and there are instructions included in the file.

---

