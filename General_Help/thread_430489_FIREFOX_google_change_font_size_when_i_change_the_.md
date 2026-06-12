---
title: "FIREFOX: google change font size when i change the default font"
date: 2007-05-02
forum: General Help
---

### Post by romaluca on 2007-05-02
Why google.com change font size when i change the default font?
How can i do to not modify the font size of google?

In other browsers when i modify the default font, google.com not change.

---

### Post by Interestedinthepenguin on 2007-05-07
Hello.  :)

The only way that I know how to fix this problem is by doing this:  

Open up userContent.css (a text file that is located in /.mozilla/firefox/yourfirefoxprofilename.default/chrome/)

Copy and paste this code into the file: 

```
@-moz-document domain(google.com) 

{
a.l {font-size: 14.4px  !important}

} 
```

Save the document, and restart your browser.

---

### Post by kerry_s on 2007-05-07
uncheck the setting that allows sites to choose there own font and it will always use your fonts.

---

