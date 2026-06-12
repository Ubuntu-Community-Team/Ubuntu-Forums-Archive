---
title: "LAMP server webpage display problems."
date: 2013-07-17
forum: General Help
---

### Post by kin37ik on 2013-07-17
i just recently installed 12.04 LTS on a dedicated server which is serving webpages and also doing MySQL backend support for game servers that require it, i have a major problem with the webpages in the lamp server not displaying correctly at all.

instead of displaying all the images specified in the CSS file for the pages, it just displays a black background with 1 coloured box, with all the white text i have written on the webpage, no images load whatsoever, i have wondered if this is because of chmod permissions? is there a fix to have the images working again?

---

### Post by SeijiSensei on 2013-07-17
Sounds more like the browser cannot read the CSS stylesheet.

What do you see in /var/log/apache2/error.log?  Any denials?

Open a page that displays incorrectly in Firefox, then right-click anywhere on the page and choose View Page Source.  You'll see the <link> directive that loads the stylesheet.  Click on the link to the stylesheet.  Does it load?

---

