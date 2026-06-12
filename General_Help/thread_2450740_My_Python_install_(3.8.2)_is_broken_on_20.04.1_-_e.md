---
title: "My Python install (3.8.2) is broken on 20.04.1 - enum/enum34 issues"
date: 2020-09-19
forum: General Help
---

### Post by mizled2 on 2020-09-19
I have a Ubuntu server install (currently 20.04.1) that I have always updated to the latest LTS over the years. I recently updated to 20.04.1 from 18.04.x but I was having this issue on 18.04.x too. This Ubuntu system is used to host a number of applications (Plex, Tautulli, certbot, and NGINX just to name a few).

The issue that I am having is with python 3.x and Tautulli. My system has python2.7 and 3.8.2 installed. When I configure Tautulli to use python 3.8.2 and start Tautulli I get a python error of [FONT=arial black]AttributeError: module 'enum' has no attribute 'IntFlag'[/FONT] and it fails to start. I have been working with the Tautulli dev on reddit and it seems there is an issue or conflict with enum34. I am not really sure how I proceed or repair my python install and also remove python 2.7 (which I no longer need because certbot and Tautulli both support python 3.x).

Here is the reddit thread where the Tautulli dev has been helping me too. [https://www.reddit.com/r/Tautulli/comments/ivvwo5/i_am_stuck_on_python_27_and_need_help/](https://www.reddit.com/r/Tautulli/comments/ivvwo5/i_am_stuck_on_python_27_and_need_help/)

What I need help with is:

1) Removing any version of enum34 that may be causing issues or repair my version of enum.
2) Remove any old version of python (specifically 2.7) and repair version 3.8.2 if necessary.

Any help would be appreciated.

---

