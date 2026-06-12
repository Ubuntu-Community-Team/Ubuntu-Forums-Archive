---
title: "customizing firefox"
date: 2007-03-10
forum: General Help
---

### Post by jfca283 on 2007-03-10
the problem is that i get a theme for gnome, which came with a userChrome.css file 
i put it in 
~/.mozilla/default/6fhhihyw.slt/chrome
but it doesn't apply the changes
i don't know what is wrong
this is ther file
```
/*
 * Edit this file and copy it as userChrome.css into your
 * profile-directory/chrome/
 */

/*
 * This file can be used to customize the look of Mozilla's user interface
 * You should consider using !important on rules which you want to
 * override default settings.
 */

/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes 20 pt:
 *
 * * {
 *   font-size: 20pt !important
 * }
 */
/*
 * Make menu items in particular 15 pt instead of the default size:
 *
 * menupopup > * {
 *   font-size: 15pt !important
 * }
 */
/*
 * Give the Location (URL) Bar a fixed-width font
 *
 * #urlbar {
 *    font-family: monospace !important;
 * }
 */

/*
 * Eliminate the throbber and its annoying movement:
 *
 * #throbber-box {
 *   display: none !important;
 * }
 */

/*
 * For more examples see http://www.mozilla.org/unix/customizing.html
 */
 
menubar > menu {
color: white;
}

menubar > menu[_moz-menuactive="true"] {
color: white;
}

menubar > menu[_moz-menuactive="true"][open="true"] {
color: black;
} 
```

any idea?

---

### Post by Tommaso on 2007-03-22
Try to add an !important near the code like this:
```

/*
 * This file can be used to customize the look of Mozilla's user interface
 * You should consider using !important on rules which you want to
 * override default settings.
 */

/*
 * Do not remove the @namespace line -- it's required for correct functioning
 */
@namespace url("http://www.mozilla.org/keymaster/gatekeeper/there.is.only.xul"); /* set default namespace to XUL */


/*
 * Some possible accessibility enhancements:
 */
/*
 * Make all the default font sizes 20 pt:
 *
 * * {
 *   font-size: 20pt !important
 * }
 */
/*
 * Make menu items in particular 15 pt instead of the default size:
 *
 * menupopup > * {
 *   font-size: 15pt !important
 * }
 */
/*
 * Give the Location (URL) Bar a fixed-width font
 *
 * #urlbar {
 *    font-family: monospace !important;
 * }
 */

/*
 * Eliminate the throbber and its annoying movement:
 *
 * #throbber-box {
 *   display: none !important;
 * }
 */

/*
 * For more examples see http://www.mozilla.org/unix/customizing.html
 */
 
menubar > menu {
color: white !important;
}

menubar > menu[_moz-menuactive="true"] {
color: white !important;
}

menubar > menu[_moz-menuactive="true"][open="true"] {
color: black !important;
} 


```

---

