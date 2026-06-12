---
title: "If You're Afraid to Lose remastersys due to repository being shut down, try this"
date: 2015-02-05
forum: General Help
---

### Post by stgparris on 2015-02-05
[FONT=arial]Everyone knows that Fragadelic has ended the project Remastersys.  He's kept the repository of his open for some time with donations.  If you happen to be lucky enough to get his repository up for the LAST version of Remastersys, there is a way to keep those deb files in case Fragadelic is unable to keep his repository up and running.  It can be done in any of the Debian/Ubuntu variants.  Follow these steps if you don't clean your apt-cache.  If you DID clean your apt-cache, you may be out of luck.

1.    Open your favorite file manager (mine being Dolphin since I'm on Kubuntu).

2.    Navigate to the folder /var/cache/apt/archives

3.    Look for the deb files remastersys-gui_3.0.4-1_amd64.deb and remastersys_3.0.4-2_all.deb
[/FONT][FONT=times new roman][FONT=arial]
4.    Copy these files from /var/cache/apt/archives to a folder of your choice via copy/paste with your file manager or use cp.

These simple steps will allow you to continue to use Remastersys till it is either replaced by yet another project as in this case the other project designed to replace Remastersys has since folded as well, or till this application can no longer be used due to dependency issues.[/FONT]
[/FONT]

---

