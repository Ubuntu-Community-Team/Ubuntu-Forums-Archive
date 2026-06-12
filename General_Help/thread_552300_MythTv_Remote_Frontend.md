---
title: "MythTv Remote Frontend"
date: 2007-09-16
forum: General Help
---

### Post by kbaum on 2007-09-16
Hi, I have MythTv set up and working on one machine (which acts as a backend and frontend). Now I want to try to add a remote frontend. I've installed the frontend, but now I'm lost. What do I do?

---

### Post by aJayRoo on 2007-09-16
I have setup a frontend only machine using the instructions from the Ubuntu community documentation pages [https://help.ubuntu.com/community/MythTV_Feisty_Frontend](https://help.ubuntu.com/community/MythTV_Feisty_Frontend) and [https://help.ubuntu.com/community/MythTV_Feisty_Backend](https://help.ubuntu.com/community/MythTV_Feisty_Backend) (the sections referring to setting up the frontend/backend respectively, you can ignore all the installation stuff of course)!
Make sure you read the page about setting up your backend machine carefully as you will need to change some of the configuration there to enable the use of a remote frontend. Everything you need should be there, MythTV can be tricky but as long as you read those pages carefully you should be fine!

---

### Post by tommyp on 2007-09-27
The key is that in the backend setup you should set the ip address of the computer that the backend is on.  One thing I discovered is to set your backend computer to a static ip address using the networking tools.  This way, your router won't change the ip address on you and break the link between remote frontend and the backend.

---

