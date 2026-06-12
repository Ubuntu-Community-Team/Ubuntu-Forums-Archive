---
title: "Firefox Menu / MurrinaDBO"
date: 2008-06-07
forum: General Help
---

### Post by HybridZero on 2008-06-07
Howdy all. I was just wondering if there's any way to force Firefox's menu bar font to a certain color? I'm currently using MurrinaDBO theme for my controls, and while the theme works great for everything else, Firefox seems to interpret the theme incorrectly and use white as it's menu font rather than the black that everything else uses.

I've attached a screenshot (Screenshot 1) to illustrate the problem: Firefox running beside Terminal, which displays the menus correctly. Any help anyone can give me would be very much appreciated.

Thanks!

**EDIT:** I modified the menubar text to be black using:

menubar, menubutton, menulist, menu {
  font-family: sans !important;
  font-size: 9pt !important;
  color: black ! important; 
}

which worked for the menubar, but now all of my submenus are also displayed as black on a black background (both bookmarks folders and submenus in other menus - Screenshot 2). How can I get the submenus back to being displayed with white text while keeping the main menu bar text as black?


**UPDATE:** I was able to solve the problem by relying on the menu ids in order to theme the menubar items only while leaving the submenu colors the way they were. Not the most elegant solution probably, but it's the only one I've found so far.

The userChrome.css looks like this:

menu#file-menu {color: black ! important;}
menu#edit-menu {color: black ! important;}
menu#view-menu {color: black ! important;}
menu#history-menu {color: black ! important;}
menu#bookmarksMenu {color: black ! important;}
menu#tools-menu {color: black ! important;}
menu#helpMenu {color: black ! important;}

---

