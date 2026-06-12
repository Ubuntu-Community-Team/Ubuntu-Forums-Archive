---
title: "Application Desktop Change"
date: 2023-11-21
forum: General Help
---

### Post by hei17 on 2023-11-21
I would like to change the Application Desktop from black to an image. I am using a Dell Latitude, Ubuntu 22.04.3 LTS, Gnome 42.9, window system Wayland, and theme Yaru. I've made changes to the panel in gnome-shell.css but do not know where to look for background to application desktop. Any help would be appreciated.

---

### Post by MAFoElffen on 2023-11-21
I think you are having a challenge to the names and nomenclature of Linux...

Do you mean your are trying to change the background image of the Desktop in the Desktop Environment? 

You do not have to edit any .css files.

Right-click on the desktop... Choose "Change Backround". That is shortcut to get to "Settings" > "Background"... Choose your background image.

---

### Post by hei17 on 2023-11-26
When you click the show applications icon in the dock, it takes you to the applications desktop with a black background by default. To replace the black with an image file I created gnome-shell.css file in /home/"user-name"/.themes/mytheme/gnome-shell. An added this code to it.
```
]#overviewGroup { 
  /*background-color: #ffc0cb;*/
  background-image: url("background-image-file"); 
   }

```

An then saved the file. Opened tweaks program choose applications from the menu and changed the shell option to mytheme. This changed the application desktop to the image I put in the gnome-shell.css file. If you don't have tweaks installed. Install it with Ubuntu Software. If you can't read the icon description with your chosen image background. You can change the text color by adding this code to the gnome-shell.css file.
```
.app-well-app.app-folder .overview-icon, .app-folder.grid-search-result .overview-icon, .app-well-app .overview-icon, .grid-search-result .overview-icon, .dash-item-container .show-apps .overview-icon, .list-search-result, .search-provider-icon, .switcher-list .item-box {
  border-radius: 12px;
  padding: 6px;
  spacing: 6px;
  border: 2px solid transparent;
  transition-duration: 100ms;
  text-align: center;
  color: #ff0000; }
  #overviewGroup.overview-icon {

``` 
Change the color: "color" ; to one that will show and be able to read on the background image.
This worked for me. Had fun!

---

