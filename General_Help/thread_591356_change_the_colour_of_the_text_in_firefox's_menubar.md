---
title: "change the colour of the text in firefox's menubar?"
date: 2007-10-25
forum: General Help
---

### Post by maduranga on 2007-10-25
can someone tell me how to change the colour of the text in Firefox's menus? I have applied a black colour theme and now text is unreadable.

---

### Post by brownbat on 2007-10-29
I added this to my userchrome.css, and it worked for the toplevel menus, and some others. It's not a comprehensive solution, but it is a start...

/* Change color on menus */
menu {
background-color: black !important;
color: white !important;
padding: 5px !important;
} 

For info on editing userchrome.css, look [here]("http://lifehacker.com/software/firefox/customize-firefox-with-userchromecss-197715.php").

---

### Post by maduranga on 2007-11-01
thanks :)

---

