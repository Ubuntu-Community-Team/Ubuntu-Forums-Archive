---
title: "a few minor issues after installing xgl/compiz"
date: 2006-08-19
forum: General Help
---

### Post by cptjaben on 2006-08-19
I recently installed xgl/compiz following [this]("http://wiki.cchtml.com/index.php/Xgl-Compiz-Dapper") guide and everything seems to be working execpt for a few minor issues. various keyboard shortcuts do not work, i can no longer right click on a window and tell it to move to a different workspace, i have to unmaximize and drag them across, synpatic won't let me install updates, when i click install it just rechecks for new updates. does anyone know what could be wrong or how to fix it? 

Thanks,
cptjaben

---

### Post by spockrock on 2006-08-19
what keyboard shortcuts dont work??

for the right click menu for the viewports you have to use the modified libwnck from the compiz repos.and as per synaptic I dunno.  You could try in terminal;
```
sudo aptitude update
```
and then 
```
sudo aptitude upgrade
```

to update your your dapper

---

### Post by Saibot on 2006-08-19
This thread has a fix for your Synaptic problem.
[http://ubuntuforums.org/showthread.php?t=239238](http://ubuntuforums.org/showthread.php?t=239238)

---

### Post by cptjaben on 2006-08-20
Thank you both, worked quite well

---

### Post by hollaburoo on 2006-08-20
as for the changing workspaces thing, compiz has this weird thing where you can't move maximized windows to another workspace.  Unmaximize them and then you can choose "move to viewport" when you right click on the titlebar.

---

