---
title: "Applications and menu gone"
date: 2013-01-23
forum: General Help
---

### Post by argoz17 on 2013-01-23
So I have a huge issue and i am not sure what happened. I updated my Ubuntu 12.04 LTS machine a few days ago. And since then i haven't done much outside of browsing the web. But I wanted to play my favorite Atari2600 emulator, so i clicked on the Ubuntu logo and brought up the dash, i went to "Apps" and nothing showed up. All my apps are gone. The menu itself is blank!

     Perhaps the update had something go wrong, I am doing a second update as i am writing this praying the problem is fixed. Any ideas what happened to my apps and app menu. All i can access is what is pined to my dock. 

Any help will be gladly accepted, thanks c:

---

### Post by papibe on 2013-01-23
Hi argoz17.

What version did you upgrade from?

Is this your first experience using the Unity desktop? 

Regards.

---

### Post by sudodus on 2013-01-23
Can you start a terminal window with the hotkey combination?

***ctrl + alt + t***

Then you can run any program from there (if you know its name). It might be worthwhile to run some repair commands.

---

### Post by argoz17 on 2013-01-23
It wasn't an upgrade, just a 200 or so megabyte update. My install was 12.04 and it is still 12.04. And no, I have been using ubuntu since 10.04LTS so I experienced Unity from 11.04. i have never encountered a problem like this...well at least a problem on just a update, if that is the problem. 

Thank you for the responce

---

### Post by argoz17 on 2013-01-23
I know I can do that but it is rather sucky doing that for every program on the computer....can the whole app menu be repaired via comand line? 

Thank you for the input

---

### Post by papibe on 2013-01-23
The thing I can think of is to reset Unity.

Take a look at the section called 'Reset Unity/Compiz' at this [tutorial]("http://www.tuxgarage.com/2011/04/missing-top-and-side-panels-in-unity.html").

Let us know how it goes.
Regards.

---

### Post by Frogs Hair on 2013-01-23
Open the terminal and try the following. ```
unity --reset
```

---

### Post by argoz17 on 2013-01-23
That did nothing, just set it all back to default...see my problem is, everything works fine..my file system, any applications I can use, desktop environment works great no issues...except the applications section on the dash is empty....it doesn't even have the filter tab, it has a search bar and a big empty dash. I am at a loss D:

---

### Post by dino99 on 2013-01-24
purge both unity & compiz, then reinstall them both starting with compiz

---

### Post by kostkon on 2013-01-24
Could you paste here the contents of the dpkg log?
```
gedit /var/log/dpkg.log
```

maybe there is something wrong with the applications lens.

---

### Post by argoz17 on 2013-01-24
```
2013-01-06 19:08:08 startup archives unpack
2013-01-06 19:08:13 install python-xlib <none> 0.14+20091101-1
2013-01-06 19:08:13 status half-installed python-xlib 0.14+20091101-1
2013-01-06 19:08:14 status triggers-pending install-info 4.13a.dfsg.1-8ubuntu2
2013-01-06 19:08:14 status half-installed python-xlib 0.14+20091101-1
2013-01-06 19:08:14 status unpacked python-xlib 0.14+20091101-1
2013-01-06 19:08:14 status unpacked python-xlib 0.14+20091101-1
2013-01-06 19:08:14 install istanbul <none> 0.2.2-8.1ubuntu2
2013-01-06 19:08:14 status half-installed istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:14 status triggers-pending bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 19:08:14 status half-installed istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:15 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-01-06 19:08:15 status half-installed istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:15 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-01-06 19:08:15 status half-installed istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:15 status triggers-pending man-db 2.6.1-2
2013-01-06 19:08:15 status half-installed istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:15 status triggers-pending gconf2 3.2.5-0ubuntu2
2013-01-06 19:08:15 status half-installed istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:15 status unpacked istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:15 status unpacked istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:15 trigproc install-info 4.13a.dfsg.1-8ubuntu2 4.13a.dfsg.1-8ubuntu2
2013-01-06 19:08:15 status half-configured install-info 4.13a.dfsg.1-8ubuntu2
2013-01-06 19:08:16 status installed install-info 4.13a.dfsg.1-8ubuntu2
2013-01-06 19:08:16 trigproc bamfdaemon 0.2.118-0ubuntu2~webapps12 0.2.118-0ubuntu2~webapps12
2013-01-06 19:08:16 status half-configured bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 19:08:16 status installed bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 19:08:16 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-01-06 19:08:16 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-01-06 19:08:17 status installed desktop-file-utils 0.20-0ubuntu3
2013-01-06 19:08:17 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-01-06 19:08:17 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-01-06 19:08:17 status installed gnome-menus 3.4.0-0ubuntu1
2013-01-06 19:08:17 trigproc man-db 2.6.1-2 2.6.1-2
2013-01-06 19:08:17 status half-configured man-db 2.6.1-2
2013-01-06 19:08:19 status installed man-db 2.6.1-2
2013-01-06 19:08:19 trigproc gconf2 3.2.5-0ubuntu2 3.2.5-0ubuntu2
2013-01-06 19:08:19 status half-configured gconf2 3.2.5-0ubuntu2
2013-01-06 19:08:23 status installed gconf2 3.2.5-0ubuntu2
2013-01-06 19:08:23 startup packages configure
2013-01-06 19:08:23 configure python-xlib 0.14+20091101-1 <none>
2013-01-06 19:08:23 status unpacked python-xlib 0.14+20091101-1
2013-01-06 19:08:23 status half-configured python-xlib 0.14+20091101-1
2013-01-06 19:08:24 status installed python-xlib 0.14+20091101-1
2013-01-06 19:08:24 status triggers-pending python-support 1.0.14ubuntu2
2013-01-06 19:08:24 configure istanbul 0.2.2-8.1ubuntu2 <none>
2013-01-06 19:08:24 status unpacked istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:24 status half-configured istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:24 status installed istanbul 0.2.2-8.1ubuntu2
2013-01-06 19:08:24 trigproc python-support 1.0.14ubuntu2 <none>
2013-01-06 19:08:24 status half-configured python-support 1.0.14ubuntu2
2013-01-06 19:08:27 status installed python-support 1.0.14ubuntu2
2013-01-06 19:11:27 startup archives unpack
2013-01-06 19:11:28 install libcgraph5 <none> 2.26.3-10ubuntu1
2013-01-06 19:11:28 status half-installed libcgraph5 2.26.3-10ubuntu1
2013-01-06 19:11:28 status unpacked libcgraph5 2.26.3-10ubuntu1
2013-01-06 19:11:28 status unpacked libcgraph5 2.26.3-10ubuntu1
2013-01-06 19:11:29 install libgvpr1 <none> 2.26.3-10ubuntu1
2013-01-06 19:11:29 status half-installed libgvpr1 2.26.3-10ubuntu1
2013-01-06 19:11:29 status unpacked libgvpr1 2.26.3-10ubuntu1
2013-01-06 19:11:29 status unpacked libgvpr1 2.26.3-10ubuntu1
2013-01-06 19:11:29 install graphviz <none> 2.26.3-10ubuntu1
2013-01-06 19:11:29 status half-installed graphviz 2.26.3-10ubuntu1
2013-01-06 19:11:30 status triggers-pending man-db 2.6.1-2
2013-01-06 19:11:30 status half-installed graphviz 2.26.3-10ubuntu1
2013-01-06 19:11:30 status unpacked graphviz 2.26.3-10ubuntu1
2013-01-06 19:11:30 status unpacked graphviz 2.26.3-10ubuntu1
2013-01-06 19:11:30 install kazam <none> 1.0.6-0ubuntu1
2013-01-06 19:11:30 status half-installed kazam 1.0.6-0ubuntu1
2013-01-06 19:11:31 status triggers-pending bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 19:11:31 status half-installed kazam 1.0.6-0ubuntu1
2013-01-06 19:11:31 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-01-06 19:11:31 status half-installed kazam 1.0.6-0ubuntu1
2013-01-06 19:11:31 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-01-06 19:11:31 status half-installed kazam 1.0.6-0ubuntu1
2013-01-06 19:11:31 status triggers-pending hicolor-icon-theme 0.12-1ubuntu2
2013-01-06 19:11:31 status half-installed kazam 1.0.6-0ubuntu1
2013-01-06 19:11:31 status unpacked kazam 1.0.6-0ubuntu1
2013-01-06 19:11:31 status unpacked kazam 1.0.6-0ubuntu1
2013-01-06 19:11:31 trigproc man-db 2.6.1-2 2.6.1-2
2013-01-06 19:11:31 status half-configured man-db 2.6.1-2
2013-01-06 19:11:33 status installed man-db 2.6.1-2
2013-01-06 19:11:33 trigproc bamfdaemon 0.2.118-0ubuntu2~webapps12 0.2.118-0ubuntu2~webapps12
2013-01-06 19:11:33 status half-configured bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 19:11:33 status installed bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 19:11:33 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-01-06 19:11:33 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-01-06 19:11:33 status installed desktop-file-utils 0.20-0ubuntu3
2013-01-06 19:11:33 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-01-06 19:11:33 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-01-06 19:11:34 status installed gnome-menus 3.4.0-0ubuntu1
2013-01-06 19:11:34 trigproc hicolor-icon-theme 0.12-1ubuntu2 0.12-1ubuntu2
2013-01-06 19:11:34 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2013-01-06 19:11:45 status installed hicolor-icon-theme 0.12-1ubuntu2
2013-01-06 19:11:45 startup packages configure
2013-01-06 19:11:45 configure libcgraph5 2.26.3-10ubuntu1 <none>
2013-01-06 19:11:45 status unpacked libcgraph5 2.26.3-10ubuntu1
2013-01-06 19:11:45 status half-configured libcgraph5 2.26.3-10ubuntu1
2013-01-06 19:11:46 status installed libcgraph5 2.26.3-10ubuntu1
2013-01-06 19:11:46 status triggers-pending libc-bin 2.15-0ubuntu10.3
2013-01-06 19:11:46 configure libgvpr1 2.26.3-10ubuntu1 <none>
2013-01-06 19:11:46 status unpacked libgvpr1 2.26.3-10ubuntu1
2013-01-06 19:11:46 status half-configured libgvpr1 2.26.3-10ubuntu1
2013-01-06 19:11:46 status installed libgvpr1 2.26.3-10ubuntu1
2013-01-06 19:11:46 configure graphviz 2.26.3-10ubuntu1 <none>
2013-01-06 19:11:46 status unpacked graphviz 2.26.3-10ubuntu1
2013-01-06 19:11:46 status half-configured graphviz 2.26.3-10ubuntu1
2013-01-06 19:11:46 status installed graphviz 2.26.3-10ubuntu1
2013-01-06 19:11:46 configure kazam 1.0.6-0ubuntu1 <none>
2013-01-06 19:11:46 status unpacked kazam 1.0.6-0ubuntu1
2013-01-06 19:11:46 status half-configured kazam 1.0.6-0ubuntu1
2013-01-06 19:11:47 status installed kazam 1.0.6-0ubuntu1
2013-01-06 19:11:47 trigproc libc-bin 2.15-0ubuntu10.3 <none>
2013-01-06 19:11:47 status half-configured libc-bin 2.15-0ubuntu10.3
2013-01-06 19:11:47 status installed libc-bin 2.15-0ubuntu10.3
2013-01-06 21:32:42 startup archives unpack
2013-01-06 21:32:43 install zsnes <none> 1.510-2.2ubuntu5
2013-01-06 21:32:43 status half-installed zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:43 status triggers-pending bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 21:32:43 status half-installed zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:43 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-01-06 21:32:43 status half-installed zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:43 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-01-06 21:32:43 status half-installed zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:43 status triggers-pending man-db 2.6.1-2
2013-01-06 21:32:43 status half-installed zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:43 status triggers-pending doc-base 0.10.3
2013-01-06 21:32:44 status half-installed zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:44 status unpacked zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:44 status unpacked zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:44 trigproc bamfdaemon 0.2.118-0ubuntu2~webapps12 0.2.118-0ubuntu2~webapps12
2013-01-06 21:32:44 status half-configured bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 21:32:44 status installed bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-06 21:32:44 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-01-06 21:32:44 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-01-06 21:32:44 status installed desktop-file-utils 0.20-0ubuntu3
2013-01-06 21:32:44 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-01-06 21:32:44 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-01-06 21:32:44 status installed gnome-menus 3.4.0-0ubuntu1
2013-01-06 21:32:44 trigproc man-db 2.6.1-2 2.6.1-2
2013-01-06 21:32:44 status half-configured man-db 2.6.1-2
2013-01-06 21:32:46 status installed man-db 2.6.1-2
2013-01-06 21:32:46 trigproc doc-base 0.10.3 0.10.3
2013-01-06 21:32:46 status half-configured doc-base 0.10.3
2013-01-06 21:32:46 status installed doc-base 0.10.3
2013-01-06 21:32:47 startup packages configure
2013-01-06 21:32:47 configure zsnes 1.510-2.2ubuntu5 <none>
2013-01-06 21:32:47 status unpacked zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:47 status half-configured zsnes 1.510-2.2ubuntu5
2013-01-06 21:32:47 status installed zsnes 1.510-2.2ubuntu5
2013-01-23 18:50:34 startup archives unpack
2013-01-23 18:50:40 upgrade dpkg 1.16.1.2ubuntu7 1.16.1.2ubuntu7.1
2013-01-23 18:50:40 status half-configured dpkg 1.16.1.2ubuntu7
2013-01-23 18:50:41 status unpacked dpkg 1.16.1.2ubuntu7
2013-01-23 18:50:41 status half-installed dpkg 1.16.1.2ubuntu7
2013-01-23 18:50:41 status triggers-pending man-db 2.6.1-2
2013-01-23 18:50:41 status half-installed dpkg 1.16.1.2ubuntu7
2013-01-23 18:50:42 status half-installed dpkg 1.16.1.2ubuntu7
2013-01-23 18:50:42 status unpacked dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:42 status unpacked dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:42 trigproc man-db 2.6.1-2 2.6.1-2
2013-01-23 18:50:42 status half-configured man-db 2.6.1-2
2013-01-23 18:50:48 status installed man-db 2.6.1-2
2013-01-23 18:50:48 startup packages configure
2013-01-23 18:50:48 configure dpkg 1.16.1.2ubuntu7.1 <none>
2013-01-23 18:50:48 status unpacked dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:49 status unpacked dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:49 status unpacked dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:49 status unpacked dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:49 status unpacked dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:49 status half-configured dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:49 status installed dpkg 1.16.1.2ubuntu7.1
2013-01-23 18:50:50 startup archives unpack
2013-01-23 18:50:50 upgrade mountall 2.36 2.36.3
2013-01-23 18:50:50 status half-configured mountall 2.36
2013-01-23 18:50:50 status unpacked mountall 2.36
2013-01-23 18:50:50 status half-installed mountall 2.36
2013-01-23 18:50:50 status triggers-pending man-db 2.6.1-2
2013-01-23 18:50:51 status half-installed mountall 2.36
2013-01-23 18:50:51 status triggers-pending ureadahead 0.100.0-12
2013-01-23 18:50:51 status half-installed mountall 2.36
2013-01-23 18:50:51 status half-installed mountall 2.36
2013-01-23 18:50:51 status unpacked mountall 2.36.3
2013-01-23 18:50:51 status unpacked mountall 2.36.3
2013-01-23 18:50:52 upgrade libfreetype6 2.4.8-1ubuntu2 2.4.8-1ubuntu2.1
2013-01-23 18:50:52 status half-configured libfreetype6 2.4.8-1ubuntu2
2013-01-23 18:50:52 status unpacked libfreetype6 2.4.8-1ubuntu2
2013-01-23 18:50:52 status half-installed libfreetype6 2.4.8-1ubuntu2
2013-01-23 18:50:52 status half-installed libfreetype6 2.4.8-1ubuntu2
2013-01-23 18:50:52 status unpacked libfreetype6 2.4.8-1ubuntu2.1
2013-01-23 18:50:52 status unpacked libfreetype6 2.4.8-1ubuntu2.1
2013-01-23 18:50:53 upgrade libnspr4 4.8.9-1ubuntu2.3 4.9.4-0ubuntu0.12.04.1
2013-01-23 18:50:53 status half-configured libnspr4 4.8.9-1ubuntu2.3
2013-01-23 18:50:53 status unpacked libnspr4 4.8.9-1ubuntu2.3
2013-01-23 18:50:53 status half-installed libnspr4 4.8.9-1ubuntu2.3
2013-01-23 18:50:53 status half-installed libnspr4 4.8.9-1ubuntu2.3
2013-01-23 18:50:53 status unpacked libnspr4 4.9.4-0ubuntu0.12.04.1
2013-01-23 18:50:53 status unpacked libnspr4 4.9.4-0ubuntu0.12.04.1
2013-01-23 18:50:53 upgrade libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu6.1 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:50:53 status half-configured libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:54 status unpacked libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:54 status half-installed libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:54 status half-installed libnss3-1d 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:54 status unpacked libnss3-1d 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:50:54 status unpacked libnss3-1d 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:50:54 upgrade libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:50:54 status half-configured libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:55 status unpacked libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:55 status half-installed libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:55 status half-installed libnss3 3.13.1.with.ckbi.1.88-1ubuntu6.1
2013-01-23 18:50:55 status unpacked libnss3 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:50:55 status unpacked libnss3 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:50:55 upgrade google-chrome-stable 23.0.1271.97-r171054 24.0.1312.56-r177594
2013-01-23 18:50:55 status half-configured google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:50:56 status unpacked google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:50:56 status half-installed google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:51:00 status half-installed google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:51:00 status triggers-pending bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:00 status half-installed google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:51:00 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-01-23 18:51:00 status half-installed google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:51:00 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-01-23 18:51:00 status half-installed google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:51:00 status half-installed google-chrome-stable 23.0.1271.97-r171054
2013-01-23 18:51:01 status unpacked google-chrome-stable 24.0.1312.56-r177594
2013-01-23 18:51:01 status unpacked google-chrome-stable 24.0.1312.56-r177594
2013-01-23 18:51:01 upgrade libbamf3-0 0.2.118-0ubuntu2~webapps12 0.2.124.2-0ubuntu1
2013-01-23 18:51:01 status half-configured libbamf3-0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:01 status unpacked libbamf3-0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:01 status half-installed libbamf3-0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:02 status half-installed libbamf3-0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:02 status unpacked libbamf3-0 0.2.124.2-0ubuntu1
2013-01-23 18:51:02 status unpacked libbamf3-0 0.2.124.2-0ubuntu1
2013-01-23 18:51:02 upgrade libbamf0 0.2.118-0ubuntu2~webapps12 0.2.124.2-0ubuntu1
2013-01-23 18:51:02 status half-configured libbamf0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:02 status unpacked libbamf0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:02 status half-installed libbamf0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:03 status half-installed libbamf0 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:03 status unpacked libbamf0 0.2.124.2-0ubuntu1
2013-01-23 18:51:03 status unpacked libbamf0 0.2.124.2-0ubuntu1
2013-01-23 18:51:03 upgrade bamfdaemon 0.2.118-0ubuntu2~webapps12 0.2.124.2-0ubuntu1
2013-01-23 18:51:03 status half-configured bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:03 status unpacked bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:03 status half-installed bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:04 status half-installed bamfdaemon 0.2.118-0ubuntu2~webapps12
2013-01-23 18:51:04 status unpacked bamfdaemon 0.2.124.2-0ubuntu1
2013-01-23 18:51:04 status unpacked bamfdaemon 0.2.124.2-0ubuntu1
2013-01-23 18:51:04 upgrade libgranite-common 0.2.0-0~r502+pkg47~precise1 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:51:04 status half-configured libgranite-common 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:04 status unpacked libgranite-common 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:04 status half-installed libgranite-common 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:04 status triggers-pending hicolor-icon-theme 0.12-1ubuntu2
2013-01-23 18:51:05 status half-installed libgranite-common 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:05 status half-installed libgranite-common 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:05 status unpacked libgranite-common 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:51:05 status unpacked libgranite-common 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:51:05 upgrade libgranite1 0.2.0-0~r502+pkg47~precise1 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:51:05 status half-configured libgranite1 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:06 status unpacked libgranite1 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:06 status half-installed libgranite1 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:06 status half-installed libgranite1 0.2.0-0~r502+pkg47~precise1
2013-01-23 18:51:06 status unpacked libgranite1 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:51:06 status unpacked libgranite1 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:51:07 upgrade libllvm3.1 3.1-1~precise1 3.1-2ubuntu1~12.04
2013-01-23 18:51:07 status half-configured libllvm3.1 3.1-1~precise1
2013-01-23 18:51:07 status unpacked libllvm3.1 3.1-1~precise1
2013-01-23 18:51:07 status half-installed libllvm3.1 3.1-1~precise1
2013-01-23 18:51:07 status half-installed libllvm3.1 3.1-1~precise1
2013-01-23 18:51:08 status unpacked libllvm3.1 3.1-2ubuntu1~12.04
2013-01-23 18:51:08 status unpacked libllvm3.1 3.1-2ubuntu1~12.04
2013-01-23 18:51:08 upgrade mysql-common 5.5.28-0ubuntu0.12.04.3 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:51:08 status half-configured mysql-common 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:08 status unpacked mysql-common 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:08 status half-installed mysql-common 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:08 status half-installed mysql-common 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:08 status unpacked mysql-common 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:51:09 status unpacked mysql-common 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:51:09 upgrade libmysqlclient18 5.5.28-0ubuntu0.12.04.3 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:51:09 status half-configured libmysqlclient18 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:09 status unpacked libmysqlclient18 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:09 status half-installed libmysqlclient18 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:09 status half-installed libmysqlclient18 5.5.28-0ubuntu0.12.04.3
2013-01-23 18:51:09 status unpacked libmysqlclient18 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:51:09 status unpacked libmysqlclient18 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:51:10 upgrade libpulse0 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:51:10 status half-configured libpulse0 1:1.1-0ubuntu15.1
2013-01-23 18:51:10 status unpacked libpulse0 1:1.1-0ubuntu15.1
2013-01-23 18:51:10 status half-installed libpulse0 1:1.1-0ubuntu15.1
2013-01-23 18:51:11 status half-installed libpulse0 1:1.1-0ubuntu15.1
2013-01-23 18:51:11 status unpacked libpulse0 1:1.1-0ubuntu15.2
2013-01-23 18:51:11 status unpacked libpulse0 1:1.1-0ubuntu15.2
2013-01-23 18:51:11 upgrade libpulse-mainloop-glib0 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:51:11 status half-configured libpulse-mainloop-glib0 1:1.1-0ubuntu15.1
2013-01-23 18:51:11 status unpacked libpulse-mainloop-glib0 1:1.1-0ubuntu15.1
2013-01-23 18:51:11 status half-installed libpulse-mainloop-glib0 1:1.1-0ubuntu15.1
2013-01-23 18:51:11 status half-installed libpulse-mainloop-glib0 1:1.1-0ubuntu15.1
2013-01-23 18:51:12 status unpacked libpulse-mainloop-glib0 1:1.1-0ubuntu15.2
2013-01-23 18:51:12 status unpacked libpulse-mainloop-glib0 1:1.1-0ubuntu15.2
2013-01-23 18:51:12 upgrade libpulsedsp 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:51:12 status half-configured libpulsedsp 1:1.1-0ubuntu15.1
2013-01-23 18:51:12 status unpacked libpulsedsp 1:1.1-0ubuntu15.1
2013-01-23 18:51:12 status half-installed libpulsedsp 1:1.1-0ubuntu15.1
2013-01-23 18:51:12 status half-installed libpulsedsp 1:1.1-0ubuntu15.1
2013-01-23 18:51:12 status unpacked libpulsedsp 1:1.1-0ubuntu15.2
2013-01-23 18:51:12 status unpacked libpulsedsp 1:1.1-0ubuntu15.2
2013-01-23 18:51:13 install linux-image-3.2.0-36-generic-pae <none> 3.2.0-36.57
2013-01-23 18:51:13 status half-installed linux-image-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:51:21 status unpacked linux-image-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:51:21 status unpacked linux-image-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:51:22 upgrade libnm-util2 0.9.4.0-0ubuntu4.1 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:22 status half-configured libnm-util2 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:22 status unpacked libnm-util2 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:22 status half-installed libnm-util2 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:22 status half-installed libnm-util2 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:22 status unpacked libnm-util2 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:22 status unpacked libnm-util2 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:23 upgrade libnm-glib4 0.9.4.0-0ubuntu4.1 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:23 status half-configured libnm-glib4 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:23 status unpacked libnm-glib4 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:23 status half-installed libnm-glib4 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:23 status half-installed libnm-glib4 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:23 status unpacked libnm-glib4 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:23 status unpacked libnm-glib4 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:24 upgrade network-manager 0.9.4.0-0ubuntu4.1 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:24 status half-configured network-manager 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:24 status unpacked network-manager 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:24 status half-installed network-manager 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:24 status half-installed network-manager 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:24 status triggers-pending ureadahead 0.100.0-12
2013-01-23 18:51:24 status half-installed network-manager 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:24 status half-installed network-manager 0.9.4.0-0ubuntu4.1
2013-01-23 18:51:25 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:25 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:51:25 upgrade openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:25 status half-configured openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:25 status unpacked openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:25 status half-installed openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:26 status half-installed openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:26 status half-installed openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:26 status half-installed openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:26 status half-installed openjdk-7-jre 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:26 status unpacked openjdk-7-jre 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:26 status unpacked openjdk-7-jre 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:27 upgrade icedtea-7-jre-cacao 7u9-2.3.3-0ubuntu1~12.04.1 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:27 status half-configured icedtea-7-jre-cacao 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:27 status unpacked icedtea-7-jre-cacao 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:27 status half-installed icedtea-7-jre-cacao 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:27 status half-installed icedtea-7-jre-cacao 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:27 status unpacked icedtea-7-jre-cacao 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:27 status unpacked icedtea-7-jre-cacao 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:27 upgrade icedtea-7-jre-jamvm 7u9-2.3.3-0ubuntu1~12.04.1 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:27 status half-configured icedtea-7-jre-jamvm 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:27 status unpacked icedtea-7-jre-jamvm 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:27 status half-installed icedtea-7-jre-jamvm 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:28 status half-installed icedtea-7-jre-jamvm 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:28 status unpacked icedtea-7-jre-jamvm 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:28 status unpacked icedtea-7-jre-jamvm 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:28 upgrade openjdk-7-jre-headless 7u9-2.3.3-0ubuntu1~12.04.1 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:28 status half-configured openjdk-7-jre-headless 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:29 status unpacked openjdk-7-jre-headless 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:29 status half-installed openjdk-7-jre-headless 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:31 status half-installed openjdk-7-jre-headless 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:31 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:31 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:32 upgrade openjdk-7-jre-lib 7u9-2.3.3-0ubuntu1~12.04.1 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:32 status half-configured openjdk-7-jre-lib 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:32 status unpacked openjdk-7-jre-lib 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:32 status half-installed openjdk-7-jre-lib 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:33 status half-installed openjdk-7-jre-lib 7u9-2.3.3-0ubuntu1~12.04.1
2013-01-23 18:51:33 status unpacked openjdk-7-jre-lib 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:33 status unpacked openjdk-7-jre-lib 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:51:33 upgrade libglu1-mesa-dev 8.0.4-0ubuntu0.2 8.0.4-0ubuntu0.3
2013-01-23 18:51:33 status half-configured libglu1-mesa-dev 8.0.4-0ubuntu0.2
2013-01-23 18:51:33 status unpacked libglu1-mesa-dev 8.0.4-0ubuntu0.2
2013-01-23 18:51:33 status half-installed libglu1-mesa-dev 8.0.4-0ubuntu0.2
2013-01-23 18:51:34 status half-installed libglu1-mesa-dev 8.0.4-0ubuntu0.2
2013-01-23 18:51:34 status unpacked libglu1-mesa-dev 8.0.4-0ubuntu0.3
2013-01-23 18:51:34 status unpacked libglu1-mesa-dev 8.0.4-0ubuntu0.3
2013-01-23 18:51:34 upgrade libglu1-mesa 8.0.4-0ubuntu0.2 8.0.4-0ubuntu0.3
2013-01-23 18:51:34 status half-configured libglu1-mesa 8.0.4-0ubuntu0.2
2013-01-23 18:51:34 status unpacked libglu1-mesa 8.0.4-0ubuntu0.2
2013-01-23 18:51:34 status half-installed libglu1-mesa 8.0.4-0ubuntu0.2
2013-01-23 18:51:35 status half-installed libglu1-mesa 8.0.4-0ubuntu0.2
2013-01-23 18:51:36 status unpacked libglu1-mesa 8.0.4-0ubuntu0.3
2013-01-23 18:51:36 status unpacked libglu1-mesa 8.0.4-0ubuntu0.3
2013-01-23 18:51:36 upgrade gpgv 1.4.11-3ubuntu2.1 1.4.11-3ubuntu2.2
2013-01-23 18:51:36 status half-configured gpgv 1.4.11-3ubuntu2.1
2013-01-23 18:51:37 status unpacked gpgv 1.4.11-3ubuntu2.1
2013-01-23 18:51:37 status half-installed gpgv 1.4.11-3ubuntu2.1
2013-01-23 18:51:37 status half-installed gpgv 1.4.11-3ubuntu2.1
2013-01-23 18:51:37 status half-installed gpgv 1.4.11-3ubuntu2.1
2013-01-23 18:51:37 status unpacked gpgv 1.4.11-3ubuntu2.2
2013-01-23 18:51:37 status unpacked gpgv 1.4.11-3ubuntu2.2
2013-01-23 18:51:37 trigproc man-db 2.6.1-2 2.6.1-2
2013-01-23 18:51:37 status half-configured man-db 2.6.1-2
2013-01-23 18:51:39 status installed man-db 2.6.1-2
2013-01-23 18:51:39 trigproc ureadahead 0.100.0-12 0.100.0-12
2013-01-23 18:51:39 status half-configured ureadahead 0.100.0-12
2013-01-23 18:51:40 status installed ureadahead 0.100.0-12
2013-01-23 18:51:40 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-01-23 18:51:40 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-01-23 18:51:40 status installed desktop-file-utils 0.20-0ubuntu3
2013-01-23 18:51:40 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-01-23 18:51:40 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-01-23 18:51:40 status installed gnome-menus 3.4.0-0ubuntu1
2013-01-23 18:51:40 trigproc hicolor-icon-theme 0.12-1ubuntu2 0.12-1ubuntu2
2013-01-23 18:51:40 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2013-01-23 18:51:52 status installed hicolor-icon-theme 0.12-1ubuntu2
2013-01-23 18:51:53 startup packages configure
2013-01-23 18:51:53 configure gpgv 1.4.11-3ubuntu2.2 <none>
2013-01-23 18:51:53 status unpacked gpgv 1.4.11-3ubuntu2.2
2013-01-23 18:51:53 status half-configured gpgv 1.4.11-3ubuntu2.2
2013-01-23 18:51:53 status installed gpgv 1.4.11-3ubuntu2.2
2013-01-23 18:51:54 startup archives unpack
2013-01-23 18:51:54 upgrade gnupg 1.4.11-3ubuntu2.1 1.4.11-3ubuntu2.2
2013-01-23 18:51:54 status half-configured gnupg 1.4.11-3ubuntu2.1
2013-01-23 18:51:54 status unpacked gnupg 1.4.11-3ubuntu2.1
2013-01-23 18:51:55 status half-installed gnupg 1.4.11-3ubuntu2.1
2013-01-23 18:51:55 status triggers-pending man-db 2.6.1-2
2013-01-23 18:51:55 status half-installed gnupg 1.4.11-3ubuntu2.1
2013-01-23 18:51:55 status triggers-pending install-info 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:51:55 status half-installed gnupg 1.4.11-3ubuntu2.1
2013-01-23 18:51:55 status half-installed gnupg 1.4.11-3ubuntu2.1
2013-01-23 18:51:55 status unpacked gnupg 1.4.11-3ubuntu2.2
2013-01-23 18:51:55 status unpacked gnupg 1.4.11-3ubuntu2.2
2013-01-23 18:51:55 trigproc man-db 2.6.1-2 2.6.1-2
2013-01-23 18:51:55 status half-configured man-db 2.6.1-2
2013-01-23 18:51:57 status installed man-db 2.6.1-2
2013-01-23 18:51:57 trigproc install-info 4.13a.dfsg.1-8ubuntu2 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:51:57 status half-configured install-info 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:51:58 status installed install-info 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:51:59 startup packages configure
2013-01-23 18:51:59 configure gnupg 1.4.11-3ubuntu2.2 <none>
2013-01-23 18:51:59 status unpacked gnupg 1.4.11-3ubuntu2.2
2013-01-23 18:51:59 status half-configured gnupg 1.4.11-3ubuntu2.2
2013-01-23 18:51:59 status installed gnupg 1.4.11-3ubuntu2.2
2013-01-23 18:52:00 startup archives unpack
2013-01-23 18:52:01 upgrade man-db 2.6.1-2 2.6.1-2ubuntu1
2013-01-23 18:52:01 status half-configured man-db 2.6.1-2
2013-01-23 18:52:01 status unpacked man-db 2.6.1-2
2013-01-23 18:52:01 status half-installed man-db 2.6.1-2
2013-01-23 18:52:01 status triggers-pending doc-base 0.10.3
2013-01-23 18:52:01 status half-installed man-db 2.6.1-2
2013-01-23 18:52:02 status half-installed man-db 2.6.1-2
2013-01-23 18:52:02 status unpacked man-db 2.6.1-2ubuntu1
2013-01-23 18:52:02 status unpacked man-db 2.6.1-2ubuntu1
2013-01-23 18:52:02 upgrade libgnome-control-center1 1:3.4.2-0ubuntu0.7 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:02 status half-configured libgnome-control-center1 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:02 status unpacked libgnome-control-center1 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:03 status half-installed libgnome-control-center1 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:03 status half-installed libgnome-control-center1 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:03 status unpacked libgnome-control-center1 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:03 status unpacked libgnome-control-center1 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:03 upgrade activity-log-manager-control-center 0.9.4-0ubuntu3.1 0.9.4-0ubuntu3.2
2013-01-23 18:52:03 status half-configured activity-log-manager-control-center 0.9.4-0ubuntu3.1
2013-01-23 18:52:03 status unpacked activity-log-manager-control-center 0.9.4-0ubuntu3.1
2013-01-23 18:52:03 status half-installed activity-log-manager-control-center 0.9.4-0ubuntu3.1
2013-01-23 18:52:03 status triggers-pending desktop-file-utils 0.20-0ubuntu3
2013-01-23 18:52:04 status half-installed activity-log-manager-control-center 0.9.4-0ubuntu3.1
2013-01-23 18:52:04 status triggers-pending gnome-menus 3.4.0-0ubuntu1
2013-01-23 18:52:04 status half-installed activity-log-manager-control-center 0.9.4-0ubuntu3.1
2013-01-23 18:52:04 status half-installed activity-log-manager-control-center 0.9.4-0ubuntu3.1
2013-01-23 18:52:04 status unpacked activity-log-manager-control-center 0.9.4-0ubuntu3.2
2013-01-23 18:52:04 status unpacked activity-log-manager-control-center 0.9.4-0ubuntu3.2
2013-01-23 18:52:04 upgrade activity-log-manager-common 0.9.4-0ubuntu3.1 0.9.4-0ubuntu3.2
2013-01-23 18:52:04 status half-configured activity-log-manager-common 0.9.4-0ubuntu3.1
2013-01-23 18:52:04 status unpacked activity-log-manager-common 0.9.4-0ubuntu3.1
2013-01-23 18:52:04 status half-installed activity-log-manager-common 0.9.4-0ubuntu3.1
2013-01-23 18:52:05 status triggers-pending hicolor-icon-theme 0.12-1ubuntu2
2013-01-23 18:52:05 status half-installed activity-log-manager-common 0.9.4-0ubuntu3.1
2013-01-23 18:52:05 status half-installed activity-log-manager-common 0.9.4-0ubuntu3.1
2013-01-23 18:52:05 status unpacked activity-log-manager-common 0.9.4-0ubuntu3.2
2013-01-23 18:52:05 status unpacked activity-log-manager-common 0.9.4-0ubuntu3.2
2013-01-23 18:52:05 upgrade python-problem-report 2.0.1-0ubuntu15.1 2.0.1-0ubuntu17.1
2013-01-23 18:52:05 status half-configured python-problem-report 2.0.1-0ubuntu15.1
2013-01-23 18:52:06 status unpacked python-problem-report 2.0.1-0ubuntu15.1
2013-01-23 18:52:06 status half-installed python-problem-report 2.0.1-0ubuntu15.1
2013-01-23 18:52:06 status half-installed python-problem-report 2.0.1-0ubuntu15.1
2013-01-23 18:52:06 status unpacked python-problem-report 2.0.1-0ubuntu17.1
2013-01-23 18:52:06 status unpacked python-problem-report 2.0.1-0ubuntu17.1
2013-01-23 18:52:06 upgrade python-apport 2.0.1-0ubuntu15.1 2.0.1-0ubuntu17.1
2013-01-23 18:52:06 status half-configured python-apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:07 status unpacked python-apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:07 status half-installed python-apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:07 status half-installed python-apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:07 status unpacked python-apport 2.0.1-0ubuntu17.1
2013-01-23 18:52:07 status unpacked python-apport 2.0.1-0ubuntu17.1
2013-01-23 18:52:08 upgrade apport 2.0.1-0ubuntu15.1 2.0.1-0ubuntu17.1
2013-01-23 18:52:08 status half-configured apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:08 status unpacked apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:08 status half-installed apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:08 status triggers-pending shared-mime-info 1.0-0ubuntu4.1
2013-01-23 18:52:08 status half-installed apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:08 status half-installed apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:09 status triggers-pending ureadahead 0.100.0-12
2013-01-23 18:52:09 status half-installed apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:09 status triggers-pending ureadahead 0.100.0-12
2013-01-23 18:52:09 status half-installed apport 2.0.1-0ubuntu15.1
2013-01-23 18:52:09 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:52:09 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:52:09 upgrade apport-gtk 2.0.1-0ubuntu15.1 2.0.1-0ubuntu17.1
2013-01-23 18:52:09 status half-configured apport-gtk 2.0.1-0ubuntu15.1
2013-01-23 18:52:09 status unpacked apport-gtk 2.0.1-0ubuntu15.1
2013-01-23 18:52:09 status half-installed apport-gtk 2.0.1-0ubuntu15.1
2013-01-23 18:52:10 status half-installed apport-gtk 2.0.1-0ubuntu15.1
2013-01-23 18:52:10 status half-installed apport-gtk 2.0.1-0ubuntu15.1
2013-01-23 18:52:10 status half-installed apport-gtk 2.0.1-0ubuntu15.1
2013-01-23 18:52:10 status unpacked apport-gtk 2.0.1-0ubuntu17.1
2013-01-23 18:52:10 status unpacked apport-gtk 2.0.1-0ubuntu17.1
2013-01-23 18:52:10 upgrade compiz-gnome 1:0.9.7.8+bzr3121-0ubuntu1 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:10 status half-configured compiz-gnome 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:11 status unpacked compiz-gnome 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:11 status half-installed compiz-gnome 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:12 status triggers-pending gconf2 3.2.5-0ubuntu2
2013-01-23 18:52:12 status half-installed compiz-gnome 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:12 status triggers-pending gconf2 3.2.5-0ubuntu2
2013-01-23 18:52:12 status half-installed compiz-gnome 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:12 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:12 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:12 upgrade compiz-plugins 1:0.9.7.8+bzr3121-0ubuntu1 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:12 status half-configured compiz-plugins 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:13 status unpacked compiz-plugins 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:13 status half-installed compiz-plugins 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:13 status half-installed compiz-plugins 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:13 status unpacked compiz-plugins 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:13 status unpacked compiz-plugins 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:13 upgrade compiz-plugins-default 1:0.9.7.8+bzr3121-0ubuntu1 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:13 status half-configured compiz-plugins-default 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:13 status unpacked compiz-plugins-default 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:14 status half-installed compiz-plugins-default 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:14 status half-installed compiz-plugins-default 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:14 status unpacked compiz-plugins-default 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:14 status unpacked compiz-plugins-default 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:14 upgrade libdecoration0 1:0.9.7.8+bzr3121-0ubuntu1 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:14 status half-configured libdecoration0 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:14 status unpacked libdecoration0 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:14 status half-installed libdecoration0 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:15 status half-installed libdecoration0 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:15 status unpacked libdecoration0 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:15 status unpacked libdecoration0 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:15 upgrade compiz-core 1:0.9.7.8+bzr3121-0ubuntu1 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:15 status half-configured compiz-core 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:15 status unpacked compiz-core 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:15 status half-installed compiz-core 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:15 status half-installed compiz-core 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:15 status half-installed compiz-core 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:16 status half-installed compiz-core 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:16 status unpacked compiz-core 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:16 status unpacked compiz-core 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:16 upgrade compiz 1:0.9.7.8+bzr3121-0ubuntu1 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:16 status half-configured compiz 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:16 status unpacked compiz 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:16 status half-installed compiz 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:16 status half-installed compiz 1:0.9.7.8+bzr3121-0ubuntu1
2013-01-23 18:52:17 status unpacked compiz 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:17 status unpacked compiz 1:0.9.7.12-0ubuntu1
2013-01-23 18:52:17 upgrade dkms 2.2.0.3-1ubuntu3 2.2.0.3-1ubuntu3.1
2013-01-23 18:52:17 status half-configured dkms 2.2.0.3-1ubuntu3
2013-01-23 18:52:17 status unpacked dkms 2.2.0.3-1ubuntu3
2013-01-23 18:52:17 status half-installed dkms 2.2.0.3-1ubuntu3
2013-01-23 18:52:17 status half-installed dkms 2.2.0.3-1ubuntu3
2013-01-23 18:52:18 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:52:18 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:52:18 upgrade duplicity 0.6.18-0ubuntu3 0.6.18-0ubuntu3.1
2013-01-23 18:52:18 status half-configured duplicity 0.6.18-0ubuntu3
2013-01-23 18:52:18 status unpacked duplicity 0.6.18-0ubuntu3
2013-01-23 18:52:18 status half-installed duplicity 0.6.18-0ubuntu3
2013-01-23 18:52:19 status half-installed duplicity 0.6.18-0ubuntu3
2013-01-23 18:52:19 status unpacked duplicity 0.6.18-0ubuntu3.1
2013-01-23 18:52:19 status unpacked duplicity 0.6.18-0ubuntu3.1
2013-01-23 18:52:19 upgrade firefox-globalmenu 17.0.1+build1-0ubuntu0.12.04.1 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:19 status half-configured firefox-globalmenu 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:19 status unpacked firefox-globalmenu 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:19 status half-installed firefox-globalmenu 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:19 status half-installed firefox-globalmenu 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:19 status unpacked firefox-globalmenu 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:20 status unpacked firefox-globalmenu 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:20 upgrade firefox 17.0.1+build1-0ubuntu0.12.04.1 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:20 status half-configured firefox 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:20 status unpacked firefox 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:20 status half-installed firefox 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:20 status half-installed firefox 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:20 status half-installed firefox 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:23 status half-installed firefox 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:23 status unpacked firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:23 status unpacked firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:23 upgrade firefox-gnome-support 17.0.1+build1-0ubuntu0.12.04.1 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:23 status half-configured firefox-gnome-support 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status unpacked firefox-gnome-support 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status half-installed firefox-gnome-support 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status half-installed firefox-gnome-support 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status unpacked firefox-gnome-support 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status unpacked firefox-gnome-support 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 upgrade firefox-locale-de 17.0.1+build1-0ubuntu0.12.04.1 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status half-configured firefox-locale-de 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status unpacked firefox-locale-de 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:24 status half-installed firefox-locale-de 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:25 status half-installed firefox-locale-de 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:25 status unpacked firefox-locale-de 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:25 status unpacked firefox-locale-de 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:25 upgrade firefox-locale-en 17.0.1+build1-0ubuntu0.12.04.1 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:25 status half-configured firefox-locale-en 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:25 status unpacked firefox-locale-en 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:25 status half-installed firefox-locale-en 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:26 status half-installed firefox-locale-en 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:26 status unpacked firefox-locale-en 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:26 status unpacked firefox-locale-en 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:26 upgrade firefox-locale-zh-hans 17.0.1+build1-0ubuntu0.12.04.1 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:26 status half-configured firefox-locale-zh-hans 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:26 status unpacked firefox-locale-zh-hans 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:26 status half-installed firefox-locale-zh-hans 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:27 status half-installed firefox-locale-zh-hans 17.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:27 status unpacked firefox-locale-zh-hans 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:27 status unpacked firefox-locale-zh-hans 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:52:27 upgrade gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.1 0.9.4.0-0ubuntu4.2
2013-01-23 18:52:27 status half-configured gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:27 status unpacked gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:27 status half-installed gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:27 status half-installed gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:28 status unpacked gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.2
2013-01-23 18:52:28 status unpacked gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.2
2013-01-23 18:52:28 upgrade gnome-control-center-data 1:3.4.2-0ubuntu0.7 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:28 status half-configured gnome-control-center-data 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:28 status unpacked gnome-control-center-data 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:28 status half-installed gnome-control-center-data 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:29 status half-installed gnome-control-center-data 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:29 status half-installed gnome-control-center-data 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:29 status unpacked gnome-control-center-data 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:29 status unpacked gnome-control-center-data 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:29 upgrade gnome-control-center 1:3.4.2-0ubuntu0.7 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:29 status half-configured gnome-control-center 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:30 status unpacked gnome-control-center 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:30 status half-installed gnome-control-center 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:30 status half-installed gnome-control-center 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:30 status half-installed gnome-control-center 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:30 status half-installed gnome-control-center 1:3.4.2-0ubuntu0.7
2013-01-23 18:52:30 status unpacked gnome-control-center 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:30 status unpacked gnome-control-center 1:3.4.2-0ubuntu0.8
2013-01-23 18:52:31 upgrade gnomine 1:3.4.1-0ubuntu2.1 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:31 status half-configured gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:31 status unpacked gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:31 status half-installed gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:31 status triggers-pending libglib2.0-0 2.32.3-0ubuntu1
2013-01-23 18:52:31 status half-installed gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:31 status half-installed gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:32 status half-installed gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:32 status half-installed gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:32 status half-installed gnomine 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:32 status unpacked gnomine 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:32 status unpacked gnomine 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:33 upgrade mahjongg 1:3.4.1-0ubuntu2.1 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:33 status half-configured mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:33 status unpacked mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:33 status half-installed mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:33 status half-installed mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:33 status half-installed mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:34 status half-installed mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:34 status half-installed mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:34 status half-installed mahjongg 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:34 status unpacked mahjongg 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:34 status unpacked mahjongg 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:35 upgrade gnome-sudoku 1:3.4.1-0ubuntu2.1 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:35 status half-configured gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:35 status unpacked gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:35 status half-installed gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:36 status half-installed gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:36 status half-installed gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:36 status half-installed gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:36 status half-installed gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:36 status half-installed gnome-sudoku 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:37 status unpacked gnome-sudoku 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:37 status unpacked gnome-sudoku 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:37 upgrade gnome-games-data 1:3.4.1-0ubuntu2.1 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:37 status half-configured gnome-games-data 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:37 status unpacked gnome-games-data 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:37 status half-installed gnome-games-data 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:37 status half-installed gnome-games-data 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:37 status half-installed gnome-games-data 1:3.4.1-0ubuntu2.1
2013-01-23 18:52:37 status unpacked gnome-games-data 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:37 status unpacked gnome-games-data 1:3.4.1-0ubuntu2.2
2013-01-23 18:52:38 upgrade grub-pc 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-23 18:52:38 status half-configured grub-pc 1.99-21ubuntu3.4
2013-01-23 18:52:38 status unpacked grub-pc 1.99-21ubuntu3.4
2013-01-23 18:52:38 status half-installed grub-pc 1.99-21ubuntu3.4
2013-01-23 18:52:39 status half-installed grub-pc 1.99-21ubuntu3.4
2013-01-23 18:52:39 status unpacked grub-pc 1.99-21ubuntu3.7
2013-01-23 18:52:39 status unpacked grub-pc 1.99-21ubuntu3.7
2013-01-23 18:52:39 upgrade grub-pc-bin 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-23 18:52:39 status half-configured grub-pc-bin 1.99-21ubuntu3.4
2013-01-23 18:52:39 status unpacked grub-pc-bin 1.99-21ubuntu3.4
2013-01-23 18:52:39 status half-installed grub-pc-bin 1.99-21ubuntu3.4
2013-01-23 18:52:40 status half-installed grub-pc-bin 1.99-21ubuntu3.4
2013-01-23 18:52:40 status unpacked grub-pc-bin 1.99-21ubuntu3.7
2013-01-23 18:52:40 status unpacked grub-pc-bin 1.99-21ubuntu3.7
2013-01-23 18:52:40 upgrade grub2-common 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-23 18:52:40 status half-configured grub2-common 1.99-21ubuntu3.4
2013-01-23 18:52:40 status unpacked grub2-common 1.99-21ubuntu3.4
2013-01-23 18:52:40 status half-installed grub2-common 1.99-21ubuntu3.4
2013-01-23 18:52:40 status triggers-pending install-info 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:52:40 status half-installed grub2-common 1.99-21ubuntu3.4
2013-01-23 18:52:41 status half-installed grub2-common 1.99-21ubuntu3.4
2013-01-23 18:52:41 status unpacked grub2-common 1.99-21ubuntu3.7
2013-01-23 18:52:41 status unpacked grub2-common 1.99-21ubuntu3.7
2013-01-23 18:52:41 upgrade grub-common 1.99-21ubuntu3.4 1.99-21ubuntu3.7
2013-01-23 18:52:41 status half-configured grub-common 1.99-21ubuntu3.4
2013-01-23 18:52:41 status unpacked grub-common 1.99-21ubuntu3.4
2013-01-23 18:52:41 status half-installed grub-common 1.99-21ubuntu3.4
2013-01-23 18:52:42 status half-installed grub-common 1.99-21ubuntu3.4
2013-01-23 18:52:42 status half-installed grub-common 1.99-21ubuntu3.4
2013-01-23 18:52:42 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:52:42 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:52:43 upgrade libnautilus-extension1a 1:3.4.2-0ubuntu5 1:3.4.2-0ubuntu6
2013-01-23 18:52:43 status half-configured libnautilus-extension1a 1:3.4.2-0ubuntu5
2013-01-23 18:52:43 status unpacked libnautilus-extension1a 1:3.4.2-0ubuntu5
2013-01-23 18:52:43 status half-installed libnautilus-extension1a 1:3.4.2-0ubuntu5
2013-01-23 18:52:43 status half-installed libnautilus-extension1a 1:3.4.2-0ubuntu5
2013-01-23 18:52:43 status unpacked libnautilus-extension1a 1:3.4.2-0ubuntu6
2013-01-23 18:52:43 status unpacked libnautilus-extension1a 1:3.4.2-0ubuntu6
2013-01-23 18:52:43 upgrade libnm-glib-vpn1 0.9.4.0-0ubuntu4.1 0.9.4.0-0ubuntu4.2
2013-01-23 18:52:43 status half-configured libnm-glib-vpn1 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:43 status unpacked libnm-glib-vpn1 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:44 status half-installed libnm-glib-vpn1 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:44 status half-installed libnm-glib-vpn1 0.9.4.0-0ubuntu4.1
2013-01-23 18:52:44 status unpacked libnm-glib-vpn1 0.9.4.0-0ubuntu4.2
2013-01-23 18:52:44 status unpacked libnm-glib-vpn1 0.9.4.0-0ubuntu4.2
2013-01-23 18:52:44 upgrade vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:44 status half-configured vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:44 status unpacked vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:44 status half-installed vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:45 status triggers-pending vlc-nox 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:45 status half-installed vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:45 status half-installed vlc-plugin-notify 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:45 status unpacked vlc-plugin-notify 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:45 status unpacked vlc-plugin-notify 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:45 upgrade vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:45 status half-configured vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:45 status unpacked vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:45 status half-installed vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:46 status half-installed vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:46 status half-installed vlc-plugin-pulse 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:46 status unpacked vlc-plugin-pulse 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:46 status unpacked vlc-plugin-pulse 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:46 upgrade vlc 2.0.3-0ubuntu0.12.04.1 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:46 status half-configured vlc 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:46 status unpacked vlc 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:46 status half-installed vlc 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:47 status half-installed vlc 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:47 status half-installed vlc 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:47 status half-installed vlc 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:47 status half-installed vlc 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:48 status unpacked vlc 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:48 status unpacked vlc 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:48 upgrade libvlccore5 2.0.3-0ubuntu0.12.04.1 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:48 status half-configured libvlccore5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:49 status unpacked libvlccore5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:49 status half-installed libvlccore5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:49 status half-installed libvlccore5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:49 status unpacked libvlccore5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:49 status unpacked libvlccore5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:50 upgrade vlc-data 2.0.3-0ubuntu0.12.04.1 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:50 status half-configured vlc-data 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:50 status unpacked vlc-data 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:50 status half-installed vlc-data 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:50 status half-installed vlc-data 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:52 status half-installed vlc-data 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:52 status unpacked vlc-data 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:52 status unpacked vlc-data 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:53 upgrade vlc-nox 2.0.3-0ubuntu0.12.04.1 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:53 status half-configured vlc-nox 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:53 status unpacked vlc-nox 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:53 status half-installed vlc-nox 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:54 status half-installed vlc-nox 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:54 status unpacked vlc-nox 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:54 status unpacked vlc-nox 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:54 upgrade libvlc5 2.0.3-0ubuntu0.12.04.1 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:54 status half-configured libvlc5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:54 status unpacked libvlc5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:54 status half-installed libvlc5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:54 status half-installed libvlc5 2.0.3-0ubuntu0.12.04.1
2013-01-23 18:52:55 status unpacked libvlc5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:55 status unpacked libvlc5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:52:55 upgrade linux-generic-pae 3.2.0.35.40 3.2.0.36.43
2013-01-23 18:52:55 status half-configured linux-generic-pae 3.2.0.35.40
2013-01-23 18:52:55 status unpacked linux-generic-pae 3.2.0.35.40
2013-01-23 18:52:55 status half-installed linux-generic-pae 3.2.0.35.40
2013-01-23 18:52:55 status half-installed linux-generic-pae 3.2.0.35.40
2013-01-23 18:52:55 status unpacked linux-generic-pae 3.2.0.36.43
2013-01-23 18:52:55 status unpacked linux-generic-pae 3.2.0.36.43
2013-01-23 18:52:56 upgrade linux-image-generic-pae 3.2.0.35.40 3.2.0.36.43
2013-01-23 18:52:56 status half-configured linux-image-generic-pae 3.2.0.35.40
2013-01-23 18:52:56 status unpacked linux-image-generic-pae 3.2.0.35.40
2013-01-23 18:52:56 status half-installed linux-image-generic-pae 3.2.0.35.40
2013-01-23 18:52:56 status half-installed linux-image-generic-pae 3.2.0.35.40
2013-01-23 18:52:56 status unpacked linux-image-generic-pae 3.2.0.36.43
2013-01-23 18:52:56 status unpacked linux-image-generic-pae 3.2.0.36.43
2013-01-23 18:52:56 install linux-headers-3.2.0-36 <none> 3.2.0-36.57
2013-01-23 18:52:56 status half-installed linux-headers-3.2.0-36 3.2.0-36.57
2013-01-23 18:53:07 status unpacked linux-headers-3.2.0-36 3.2.0-36.57
2013-01-23 18:53:08 status unpacked linux-headers-3.2.0-36 3.2.0-36.57
2013-01-23 18:53:08 install linux-headers-3.2.0-36-generic-pae <none> 3.2.0-36.57
2013-01-23 18:53:08 status half-installed linux-headers-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:53:10 status unpacked linux-headers-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:53:10 status unpacked linux-headers-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:53:11 upgrade linux-headers-generic-pae 3.2.0.35.40 3.2.0.36.43
2013-01-23 18:53:11 status half-configured linux-headers-generic-pae 3.2.0.35.40
2013-01-23 18:53:11 status unpacked linux-headers-generic-pae 3.2.0.35.40
2013-01-23 18:53:11 status half-installed linux-headers-generic-pae 3.2.0.35.40
2013-01-23 18:53:11 status half-installed linux-headers-generic-pae 3.2.0.35.40
2013-01-23 18:53:11 status unpacked linux-headers-generic-pae 3.2.0.36.43
2013-01-23 18:53:11 status unpacked linux-headers-generic-pae 3.2.0.36.43
2013-01-23 18:53:11 upgrade linux-libc-dev 3.2.0-35.55 3.2.0-36.57
2013-01-23 18:53:11 status half-configured linux-libc-dev 3.2.0-35.55
2013-01-23 18:53:11 status unpacked linux-libc-dev 3.2.0-35.55
2013-01-23 18:53:12 status half-installed linux-libc-dev 3.2.0-35.55
2013-01-23 18:53:12 status half-installed linux-libc-dev 3.2.0-35.55
2013-01-23 18:53:12 status unpacked linux-libc-dev 3.2.0-36.57
2013-01-23 18:53:12 status unpacked linux-libc-dev 3.2.0-36.57
2013-01-23 18:53:13 upgrade nautilus-data 1:3.4.2-0ubuntu5 1:3.4.2-0ubuntu6
2013-01-23 18:53:13 status half-configured nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:13 status unpacked nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:13 status half-installed nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:13 status half-installed nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:13 status triggers-pending gconf2 3.2.5-0ubuntu2
2013-01-23 18:53:13 status half-installed nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:13 status half-installed nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:13 status half-installed nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:13 status half-installed nautilus-data 1:3.4.2-0ubuntu5
2013-01-23 18:53:14 status unpacked nautilus-data 1:3.4.2-0ubuntu6
2013-01-23 18:53:14 status unpacked nautilus-data 1:3.4.2-0ubuntu6
2013-01-23 18:53:14 upgrade nautilus 1:3.4.2-0ubuntu5 1:3.4.2-0ubuntu6
2013-01-23 18:53:14 status half-configured nautilus 1:3.4.2-0ubuntu5
2013-01-23 18:53:14 status unpacked nautilus 1:3.4.2-0ubuntu5
2013-01-23 18:53:14 status half-installed nautilus 1:3.4.2-0ubuntu5
2013-01-23 18:53:14 status half-installed nautilus 1:3.4.2-0ubuntu5
2013-01-23 18:53:14 status half-installed nautilus 1:3.4.2-0ubuntu5
2013-01-23 18:53:15 status half-installed nautilus 1:3.4.2-0ubuntu5
2013-01-23 18:53:15 status half-installed nautilus 1:3.4.2-0ubuntu5
2013-01-23 18:53:15 status unpacked nautilus 1:3.4.2-0ubuntu6
2013-01-23 18:53:15 status unpacked nautilus 1:3.4.2-0ubuntu6
2013-01-23 18:53:15 upgrade pulseaudio-utils 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:53:15 status half-configured pulseaudio-utils 1:1.1-0ubuntu15.1
2013-01-23 18:53:15 status unpacked pulseaudio-utils 1:1.1-0ubuntu15.1
2013-01-23 18:53:15 status half-installed pulseaudio-utils 1:1.1-0ubuntu15.1
2013-01-23 18:53:16 status half-installed pulseaudio-utils 1:1.1-0ubuntu15.1
2013-01-23 18:53:16 status unpacked pulseaudio-utils 1:1.1-0ubuntu15.2
2013-01-23 18:53:16 status unpacked pulseaudio-utils 1:1.1-0ubuntu15.2
2013-01-23 18:53:16 upgrade pulseaudio 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:53:16 status half-configured pulseaudio 1:1.1-0ubuntu15.1
2013-01-23 18:53:16 status unpacked pulseaudio 1:1.1-0ubuntu15.1
2013-01-23 18:53:17 status half-installed pulseaudio 1:1.1-0ubuntu15.1
2013-01-23 18:53:17 status half-installed pulseaudio 1:1.1-0ubuntu15.1
2013-01-23 18:53:17 status half-installed pulseaudio 1:1.1-0ubuntu15.1
2013-01-23 18:53:17 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:53:17 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:53:17 upgrade pulseaudio-module-gconf 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:53:17 status half-configured pulseaudio-module-gconf 1:1.1-0ubuntu15.1
2013-01-23 18:53:18 status unpacked pulseaudio-module-gconf 1:1.1-0ubuntu15.1
2013-01-23 18:53:18 status half-installed pulseaudio-module-gconf 1:1.1-0ubuntu15.1
2013-01-23 18:53:18 status half-installed pulseaudio-module-gconf 1:1.1-0ubuntu15.1
2013-01-23 18:53:18 status unpacked pulseaudio-module-gconf 1:1.1-0ubuntu15.2
2013-01-23 18:53:18 status unpacked pulseaudio-module-gconf 1:1.1-0ubuntu15.2
2013-01-23 18:53:18 upgrade pulseaudio-module-x11 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:53:18 status half-configured pulseaudio-module-x11 1:1.1-0ubuntu15.1
2013-01-23 18:53:18 status unpacked pulseaudio-module-x11 1:1.1-0ubuntu15.1
2013-01-23 18:53:18 status half-installed pulseaudio-module-x11 1:1.1-0ubuntu15.1
2013-01-23 18:53:18 status half-installed pulseaudio-module-x11 1:1.1-0ubuntu15.1
2013-01-23 18:53:19 status unpacked pulseaudio-module-x11 1:1.1-0ubuntu15.2
2013-01-23 18:53:19 status unpacked pulseaudio-module-x11 1:1.1-0ubuntu15.2
2013-01-23 18:53:19 upgrade software-center 5.2.6 5.2.7
2013-01-23 18:53:19 status half-configured software-center 5.2.6
2013-01-23 18:53:19 status unpacked software-center 5.2.6
2013-01-23 18:53:19 status half-installed software-center 5.2.6
2013-01-23 18:53:20 status half-installed software-center 5.2.6
2013-01-23 18:53:20 status half-installed software-center 5.2.6
2013-01-23 18:53:20 status half-installed software-center 5.2.6
2013-01-23 18:53:20 status half-installed software-center 5.2.6
2013-01-23 18:53:21 status unpacked software-center 5.2.7
2013-01-23 18:53:21 status unpacked software-center 5.2.7
2013-01-23 18:53:21 upgrade steam 1.0.0.18 1.0.0.22
2013-01-23 18:53:21 status half-configured steam 1.0.0.18
2013-01-23 18:53:21 status unpacked steam 1.0.0.18
2013-01-23 18:53:21 status half-installed steam 1.0.0.18
2013-01-23 18:53:21 status half-installed steam 1.0.0.18
2013-01-23 18:53:21 status half-installed steam 1.0.0.18
2013-01-23 18:53:21 status half-installed steam 1.0.0.18
2013-01-23 18:53:22 status half-installed steam 1.0.0.18
2013-01-23 18:53:22 status unpacked steam 1.0.0.22
2013-01-23 18:53:22 status unpacked steam 1.0.0.22
2013-01-23 18:53:22 upgrade thunderbird-globalmenu 17.0+build2-0ubuntu0.12.04.1 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:22 status half-configured thunderbird-globalmenu 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:22 status unpacked thunderbird-globalmenu 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:22 status half-installed thunderbird-globalmenu 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:22 status half-installed thunderbird-globalmenu 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:22 status unpacked thunderbird-globalmenu 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:23 status unpacked thunderbird-globalmenu 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:23 upgrade thunderbird 17.0+build2-0ubuntu0.12.04.1 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:23 status half-configured thunderbird 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:23 status unpacked thunderbird 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:23 status half-installed thunderbird 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:25 status half-installed thunderbird 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:25 status half-installed thunderbird 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:27 status half-installed thunderbird 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:27 status unpacked thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:27 status unpacked thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:27 upgrade thunderbird-gnome-support 17.0+build2-0ubuntu0.12.04.1 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:27 status half-configured thunderbird-gnome-support 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:28 status unpacked thunderbird-gnome-support 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:28 status half-installed thunderbird-gnome-support 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:28 status half-installed thunderbird-gnome-support 17.0+build2-0ubuntu0.12.04.1
2013-01-23 18:53:28 status unpacked thunderbird-gnome-support 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:28 status unpacked thunderbird-gnome-support 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:53:29 upgrade unattended-upgrades 0.76 0.76ubuntu1
2013-01-23 18:53:29 status half-configured unattended-upgrades 0.76
2013-01-23 18:53:29 status unpacked unattended-upgrades 0.76
2013-01-23 18:53:29 status half-installed unattended-upgrades 0.76
2013-01-23 18:53:29 status half-installed unattended-upgrades 0.76
2013-01-23 18:53:29 status half-installed unattended-upgrades 0.76
2013-01-23 18:53:29 status unpacked unattended-upgrades 0.76ubuntu1
2013-01-23 18:53:29 status unpacked unattended-upgrades 0.76ubuntu1
2013-01-23 18:53:30 upgrade vino 3.4.2-0ubuntu1.1 3.4.2-0ubuntu1.2
2013-01-23 18:53:30 status half-configured vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:30 status unpacked vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:30 status half-installed vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:30 status half-installed vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:30 status half-installed vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:30 status half-installed vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:30 status half-installed vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:30 status half-installed vino 3.4.2-0ubuntu1.1
2013-01-23 18:53:31 status unpacked vino 3.4.2-0ubuntu1.2
2013-01-23 18:53:31 status unpacked vino 3.4.2-0ubuntu1.2
2013-01-23 18:53:32 upgrade x11-common 1:7.6+12ubuntu1 1:7.6+12ubuntu2
2013-01-23 18:53:32 status half-configured x11-common 1:7.6+12ubuntu1
2013-01-23 18:53:33 status unpacked x11-common 1:7.6+12ubuntu1
2013-01-23 18:53:33 status half-installed x11-common 1:7.6+12ubuntu1
2013-01-23 18:53:34 status half-installed x11-common 1:7.6+12ubuntu1
2013-01-23 18:53:34 status half-installed x11-common 1:7.6+12ubuntu1
2013-01-23 18:53:34 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:53:34 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:53:34 upgrade x11proto-dri2-dev 2.6-2 2.8-1~precise1
2013-01-23 18:53:34 status half-configured x11proto-dri2-dev 2.6-2
2013-01-23 18:53:34 status unpacked x11proto-dri2-dev 2.6-2
2013-01-23 18:53:34 status half-installed x11proto-dri2-dev 2.6-2
2013-01-23 18:53:35 status half-installed x11proto-dri2-dev 2.6-2
2013-01-23 18:53:35 status unpacked x11proto-dri2-dev 2.8-1~precise1
2013-01-23 18:53:35 status unpacked x11proto-dri2-dev 2.8-1~precise1
2013-01-23 18:53:35 upgrade x11proto-gl-dev 1.4.14-2 1.4.16-1~precise1
2013-01-23 18:53:35 status half-configured x11proto-gl-dev 1.4.14-2
2013-01-23 18:53:35 status unpacked x11proto-gl-dev 1.4.14-2
2013-01-23 18:53:35 status half-installed x11proto-gl-dev 1.4.14-2
2013-01-23 18:53:36 status half-installed x11proto-gl-dev 1.4.14-2
2013-01-23 18:53:36 status unpacked x11proto-gl-dev 1.4.16-1~precise1
2013-01-23 18:53:36 status unpacked x11proto-gl-dev 1.4.16-1~precise1
2013-01-23 18:53:36 upgrade xserver-xorg-video-all 1:7.6+12ubuntu1 1:7.6+12ubuntu2
2013-01-23 18:53:36 status half-configured xserver-xorg-video-all 1:7.6+12ubuntu1
2013-01-23 18:53:36 status unpacked xserver-xorg-video-all 1:7.6+12ubuntu1
2013-01-23 18:53:36 status half-installed xserver-xorg-video-all 1:7.6+12ubuntu1
2013-01-23 18:53:36 status half-installed xserver-xorg-video-all 1:7.6+12ubuntu1
2013-01-23 18:53:36 status unpacked xserver-xorg-video-all 1:7.6+12ubuntu2
2013-01-23 18:53:36 status unpacked xserver-xorg-video-all 1:7.6+12ubuntu2
2013-01-23 18:53:37 upgrade xserver-xorg-input-all 1:7.6+12ubuntu1 1:7.6+12ubuntu2
2013-01-23 18:53:37 status half-configured xserver-xorg-input-all 1:7.6+12ubuntu1
2013-01-23 18:53:37 status unpacked xserver-xorg-input-all 1:7.6+12ubuntu1
2013-01-23 18:53:37 status half-installed xserver-xorg-input-all 1:7.6+12ubuntu1
2013-01-23 18:53:37 status half-installed xserver-xorg-input-all 1:7.6+12ubuntu1
2013-01-23 18:53:37 status unpacked xserver-xorg-input-all 1:7.6+12ubuntu2
2013-01-23 18:53:37 status unpacked xserver-xorg-input-all 1:7.6+12ubuntu2
2013-01-23 18:53:38 upgrade xserver-xorg 1:7.6+12ubuntu1 1:7.6+12ubuntu2
2013-01-23 18:53:38 status half-configured xserver-xorg 1:7.6+12ubuntu1
2013-01-23 18:53:38 status unpacked xserver-xorg 1:7.6+12ubuntu1
2013-01-23 18:53:38 status half-installed xserver-xorg 1:7.6+12ubuntu1
2013-01-23 18:53:39 status half-installed xserver-xorg 1:7.6+12ubuntu1
2013-01-23 18:53:39 status unpacked xserver-xorg 1:7.6+12ubuntu2
2013-01-23 18:53:39 status unpacked xserver-xorg 1:7.6+12ubuntu2
2013-01-23 18:53:39 upgrade xorg 1:7.6+12ubuntu1 1:7.6+12ubuntu2
2013-01-23 18:53:39 status half-configured xorg 1:7.6+12ubuntu1
2013-01-23 18:53:39 status unpacked xorg 1:7.6+12ubuntu1
2013-01-23 18:53:39 status half-installed xorg 1:7.6+12ubuntu1
2013-01-23 18:53:39 status half-installed xorg 1:7.6+12ubuntu1
2013-01-23 18:53:40 status unpacked xorg 1:7.6+12ubuntu2
2013-01-23 18:53:40 status unpacked xorg 1:7.6+12ubuntu2
2013-01-23 18:53:40 upgrade pulseaudio-module-bluetooth 1:1.1-0ubuntu15.1 1:1.1-0ubuntu15.2
2013-01-23 18:53:40 status half-configured pulseaudio-module-bluetooth 1:1.1-0ubuntu15.1
2013-01-23 18:53:40 status unpacked pulseaudio-module-bluetooth 1:1.1-0ubuntu15.1
2013-01-23 18:53:40 status half-installed pulseaudio-module-bluetooth 1:1.1-0ubuntu15.1
2013-01-23 18:53:40 status half-installed pulseaudio-module-bluetooth 1:1.1-0ubuntu15.1
2013-01-23 18:53:40 status unpacked pulseaudio-module-bluetooth 1:1.1-0ubuntu15.2
2013-01-23 18:53:40 status unpacked pulseaudio-module-bluetooth 1:1.1-0ubuntu15.2
2013-01-23 18:53:40 trigproc doc-base 0.10.3 0.10.3
2013-01-23 18:53:40 status half-configured doc-base 0.10.3
2013-01-23 18:53:41 status installed doc-base 0.10.3
2013-01-23 18:53:41 trigproc desktop-file-utils 0.20-0ubuntu3 0.20-0ubuntu3
2013-01-23 18:53:41 status half-configured desktop-file-utils 0.20-0ubuntu3
2013-01-23 18:53:41 status installed desktop-file-utils 0.20-0ubuntu3
2013-01-23 18:53:41 trigproc gnome-menus 3.4.0-0ubuntu1 3.4.0-0ubuntu1
2013-01-23 18:53:41 status half-configured gnome-menus 3.4.0-0ubuntu1
2013-01-23 18:53:41 status installed gnome-menus 3.4.0-0ubuntu1
2013-01-23 18:53:41 trigproc hicolor-icon-theme 0.12-1ubuntu2 0.12-1ubuntu2
2013-01-23 18:53:41 status half-configured hicolor-icon-theme 0.12-1ubuntu2
2013-01-23 18:53:43 status installed hicolor-icon-theme 0.12-1ubuntu2
2013-01-23 18:53:43 trigproc shared-mime-info 1.0-0ubuntu4.1 1.0-0ubuntu4.1
2013-01-23 18:53:43 status half-configured shared-mime-info 1.0-0ubuntu4.1
2013-01-23 18:53:44 status installed shared-mime-info 1.0-0ubuntu4.1
2013-01-23 18:53:45 trigproc ureadahead 0.100.0-12 0.100.0-12
2013-01-23 18:53:45 status half-configured ureadahead 0.100.0-12
2013-01-23 18:53:45 status installed ureadahead 0.100.0-12
2013-01-23 18:53:45 trigproc gconf2 3.2.5-0ubuntu2 3.2.5-0ubuntu2
2013-01-23 18:53:45 status half-configured gconf2 3.2.5-0ubuntu2
2013-01-23 18:53:48 status installed gconf2 3.2.5-0ubuntu2
2013-01-23 18:53:49 trigproc libglib2.0-0 2.32.3-0ubuntu1 2.32.3-0ubuntu1
2013-01-23 18:53:49 status half-configured libglib2.0-0 2.32.3-0ubuntu1
2013-01-23 18:53:50 status installed libglib2.0-0 2.32.3-0ubuntu1
2013-01-23 18:53:50 trigproc install-info 4.13a.dfsg.1-8ubuntu2 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:53:50 status half-configured install-info 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:53:50 status installed install-info 4.13a.dfsg.1-8ubuntu2
2013-01-23 18:53:51 startup packages configure
2013-01-23 18:53:51 configure mountall 2.36.3 <none>
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:51 status unpacked mountall 2.36.3
2013-01-23 18:53:52 status unpacked mountall 2.36.3
2013-01-23 18:53:52 status unpacked mountall 2.36.3
2013-01-23 18:53:52 status unpacked mountall 2.36.3
2013-01-23 18:53:52 status half-configured mountall 2.36.3
2013-01-23 18:53:52 status installed mountall 2.36.3
2013-01-23 18:53:52 configure libfreetype6 2.4.8-1ubuntu2.1 <none>
2013-01-23 18:53:52 status unpacked libfreetype6 2.4.8-1ubuntu2.1
2013-01-23 18:53:52 status half-configured libfreetype6 2.4.8-1ubuntu2.1
2013-01-23 18:53:52 status installed libfreetype6 2.4.8-1ubuntu2.1
2013-01-23 18:53:52 status triggers-pending libc-bin 2.15-0ubuntu10.3
2013-01-23 18:53:52 configure libnspr4 4.9.4-0ubuntu0.12.04.1 <none>
2013-01-23 18:53:52 status unpacked libnspr4 4.9.4-0ubuntu0.12.04.1
2013-01-23 18:53:53 status half-configured libnspr4 4.9.4-0ubuntu0.12.04.1
2013-01-23 18:53:53 status installed libnspr4 4.9.4-0ubuntu0.12.04.1
2013-01-23 18:53:53 configure libnss3 3.14.1-0ckbi1.93ubuntu.0.12.04.1 <none>
2013-01-23 18:53:53 status unpacked libnss3 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:53:53 status half-configured libnss3 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:53:53 status installed libnss3 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:53:53 configure libnss3-1d 3.14.1-0ckbi1.93ubuntu.0.12.04.1 <none>
2013-01-23 18:53:53 status unpacked libnss3-1d 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:53:53 status half-configured libnss3-1d 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:53:53 status installed libnss3-1d 3.14.1-0ckbi1.93ubuntu.0.12.04.1
2013-01-23 18:53:53 configure google-chrome-stable 24.0.1312.56-r177594 <none>
2013-01-23 18:53:53 status unpacked google-chrome-stable 24.0.1312.56-r177594
2013-01-23 18:53:53 status half-configured google-chrome-stable 24.0.1312.56-r177594
2013-01-23 18:54:02 status installed google-chrome-stable 24.0.1312.56-r177594
2013-01-23 18:54:02 configure bamfdaemon 0.2.124.2-0ubuntu1 <none>
2013-01-23 18:54:02 status unpacked bamfdaemon 0.2.124.2-0ubuntu1
2013-01-23 18:54:02 status half-configured bamfdaemon 0.2.124.2-0ubuntu1
2013-01-23 18:54:02 status installed bamfdaemon 0.2.124.2-0ubuntu1
2013-01-23 18:54:02 configure libbamf3-0 0.2.124.2-0ubuntu1 <none>
2013-01-23 18:54:02 status unpacked libbamf3-0 0.2.124.2-0ubuntu1
2013-01-23 18:54:02 status half-configured libbamf3-0 0.2.124.2-0ubuntu1
2013-01-23 18:54:03 status installed libbamf3-0 0.2.124.2-0ubuntu1
2013-01-23 18:54:04 configure libbamf0 0.2.124.2-0ubuntu1 <none>
2013-01-23 18:54:04 status unpacked libbamf0 0.2.124.2-0ubuntu1
2013-01-23 18:54:04 status half-configured libbamf0 0.2.124.2-0ubuntu1
2013-01-23 18:54:04 status installed libbamf0 0.2.124.2-0ubuntu1
2013-01-23 18:54:04 configure libgranite-common 0.2.0-0~r519+pkg47~precise1 <none>
2013-01-23 18:54:04 status unpacked libgranite-common 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:54:04 status half-configured libgranite-common 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:54:04 status installed libgranite-common 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:54:04 configure libgranite1 0.2.0-0~r519+pkg47~precise1 <none>
2013-01-23 18:54:04 status unpacked libgranite1 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:54:04 status half-configured libgranite1 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:54:04 status installed libgranite1 0.2.0-0~r519+pkg47~precise1
2013-01-23 18:54:04 configure libllvm3.1 3.1-2ubuntu1~12.04 <none>
2013-01-23 18:54:04 status unpacked libllvm3.1 3.1-2ubuntu1~12.04
2013-01-23 18:54:04 status half-configured libllvm3.1 3.1-2ubuntu1~12.04
2013-01-23 18:54:05 status installed libllvm3.1 3.1-2ubuntu1~12.04
2013-01-23 18:54:05 configure mysql-common 5.5.29-0ubuntu0.12.04.1 <none>
2013-01-23 18:54:05 status unpacked mysql-common 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:54:05 status unpacked mysql-common 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:54:05 status half-configured mysql-common 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:54:05 status installed mysql-common 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:54:05 configure libmysqlclient18 5.5.29-0ubuntu0.12.04.1 <none>
2013-01-23 18:54:05 status unpacked libmysqlclient18 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:54:05 status half-configured libmysqlclient18 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:54:05 status installed libmysqlclient18 5.5.29-0ubuntu0.12.04.1
2013-01-23 18:54:05 configure libpulse0 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:54:05 status unpacked libpulse0 1:1.1-0ubuntu15.2
2013-01-23 18:54:05 status unpacked libpulse0 1:1.1-0ubuntu15.2
2013-01-23 18:54:05 status half-configured libpulse0 1:1.1-0ubuntu15.2
2013-01-23 18:54:05 status installed libpulse0 1:1.1-0ubuntu15.2
2013-01-23 18:54:05 configure libpulse-mainloop-glib0 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:54:05 status unpacked libpulse-mainloop-glib0 1:1.1-0ubuntu15.2
2013-01-23 18:54:06 status half-configured libpulse-mainloop-glib0 1:1.1-0ubuntu15.2
2013-01-23 18:54:06 status installed libpulse-mainloop-glib0 1:1.1-0ubuntu15.2
2013-01-23 18:54:06 configure libpulsedsp 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:54:06 status unpacked libpulsedsp 1:1.1-0ubuntu15.2
2013-01-23 18:54:06 status half-configured libpulsedsp 1:1.1-0ubuntu15.2
2013-01-23 18:54:06 status installed libpulsedsp 1:1.1-0ubuntu15.2
2013-01-23 18:54:06 configure linux-image-3.2.0-36-generic-pae 3.2.0-36.57 <none>
2013-01-23 18:54:06 status unpacked linux-image-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:54:06 status half-configured linux-image-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:55:12 status installed linux-image-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:55:12 configure libnm-util2 0.9.4.0-0ubuntu4.2 <none>
2013-01-23 18:55:12 status unpacked libnm-util2 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status half-configured libnm-util2 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status installed libnm-util2 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 configure libnm-glib4 0.9.4.0-0ubuntu4.2 <none>
2013-01-23 18:55:13 status unpacked libnm-glib4 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status half-configured libnm-glib4 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status installed libnm-glib4 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 configure network-manager 0.9.4.0-0ubuntu4.2 <none>
2013-01-23 18:55:13 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:13 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:14 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:14 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:14 status unpacked network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:14 status half-configured network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:14 status installed network-manager 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:14 configure libglu1-mesa 8.0.4-0ubuntu0.3 <none>
2013-01-23 18:55:14 status unpacked libglu1-mesa 8.0.4-0ubuntu0.3
2013-01-23 18:55:14 status half-configured libglu1-mesa 8.0.4-0ubuntu0.3
2013-01-23 18:55:14 status installed libglu1-mesa 8.0.4-0ubuntu0.3
2013-01-23 18:55:14 configure libglu1-mesa-dev 8.0.4-0ubuntu0.3 <none>
2013-01-23 18:55:14 status unpacked libglu1-mesa-dev 8.0.4-0ubuntu0.3
2013-01-23 18:55:14 status half-configured libglu1-mesa-dev 8.0.4-0ubuntu0.3
2013-01-23 18:55:15 status installed libglu1-mesa-dev 8.0.4-0ubuntu0.3
2013-01-23 18:55:15 configure man-db 2.6.1-2ubuntu1 <none>
2013-01-23 18:55:15 status unpacked man-db 2.6.1-2ubuntu1
2013-01-23 18:55:15 status unpacked man-db 2.6.1-2ubuntu1
2013-01-23 18:55:15 status unpacked man-db 2.6.1-2ubuntu1
2013-01-23 18:55:15 status unpacked man-db 2.6.1-2ubuntu1
2013-01-23 18:55:15 status half-configured man-db 2.6.1-2ubuntu1
2013-01-23 18:55:20 status installed man-db 2.6.1-2ubuntu1
2013-01-23 18:55:20 configure libgnome-control-center1 1:3.4.2-0ubuntu0.8 <none>
2013-01-23 18:55:20 status unpacked libgnome-control-center1 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:20 status half-configured libgnome-control-center1 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:20 status installed libgnome-control-center1 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:20 configure activity-log-manager-common 0.9.4-0ubuntu3.2 <none>
2013-01-23 18:55:20 status unpacked activity-log-manager-common 0.9.4-0ubuntu3.2
2013-01-23 18:55:20 status half-configured activity-log-manager-common 0.9.4-0ubuntu3.2
2013-01-23 18:55:20 status installed activity-log-manager-common 0.9.4-0ubuntu3.2
2013-01-23 18:55:20 configure activity-log-manager-control-center 0.9.4-0ubuntu3.2 <none>
2013-01-23 18:55:20 status unpacked activity-log-manager-control-center 0.9.4-0ubuntu3.2
2013-01-23 18:55:20 status unpacked activity-log-manager-control-center 0.9.4-0ubuntu3.2
2013-01-23 18:55:20 status half-configured activity-log-manager-control-center 0.9.4-0ubuntu3.2
2013-01-23 18:55:21 status installed activity-log-manager-control-center 0.9.4-0ubuntu3.2
2013-01-23 18:55:21 configure python-problem-report 2.0.1-0ubuntu17.1 <none>
2013-01-23 18:55:21 status unpacked python-problem-report 2.0.1-0ubuntu17.1
2013-01-23 18:55:21 status half-configured python-problem-report 2.0.1-0ubuntu17.1
2013-01-23 18:55:21 status installed python-problem-report 2.0.1-0ubuntu17.1
2013-01-23 18:55:21 configure python-apport 2.0.1-0ubuntu17.1 <none>
2013-01-23 18:55:21 status unpacked python-apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:21 status unpacked python-apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:21 status half-configured python-apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status installed python-apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 configure apport 2.0.1-0ubuntu17.1 <none>
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status unpacked apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:22 status half-configured apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:23 status installed apport 2.0.1-0ubuntu17.1
2013-01-23 18:55:23 configure apport-gtk 2.0.1-0ubuntu17.1 <none>
2013-01-23 18:55:23 status unpacked apport-gtk 2.0.1-0ubuntu17.1
2013-01-23 18:55:23 status half-configured apport-gtk 2.0.1-0ubuntu17.1
2013-01-23 18:55:23 status installed apport-gtk 2.0.1-0ubuntu17.1
2013-01-23 18:55:23 configure libdecoration0 1:0.9.7.12-0ubuntu1 <none>
2013-01-23 18:55:23 status unpacked libdecoration0 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:23 status half-configured libdecoration0 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:23 status installed libdecoration0 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:23 configure compiz-core 1:0.9.7.12-0ubuntu1 <none>
2013-01-23 18:55:23 status unpacked compiz-core 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:23 status half-configured compiz-core 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:23 status installed compiz-core 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:23 configure compiz-plugins-default 1:0.9.7.12-0ubuntu1 <none>
2013-01-23 18:55:23 status unpacked compiz-plugins-default 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status half-configured compiz-plugins-default 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status installed compiz-plugins-default 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 configure compiz-gnome 1:0.9.7.12-0ubuntu1 <none>
2013-01-23 18:55:24 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status unpacked compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status half-configured compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status installed compiz-gnome 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 configure compiz-plugins 1:0.9.7.12-0ubuntu1 <none>
2013-01-23 18:55:24 status unpacked compiz-plugins 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status half-configured compiz-plugins 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status installed compiz-plugins 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 configure compiz 1:0.9.7.12-0ubuntu1 <none>
2013-01-23 18:55:24 status unpacked compiz 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status half-configured compiz 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:24 status installed compiz 1:0.9.7.12-0ubuntu1
2013-01-23 18:55:25 configure dkms 2.2.0.3-1ubuntu3.1 <none>
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:25 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:26 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:26 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:26 status unpacked dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:26 status half-configured dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:26 status installed dkms 2.2.0.3-1ubuntu3.1
2013-01-23 18:55:26 configure duplicity 0.6.18-0ubuntu3.1 <none>
2013-01-23 18:55:26 status unpacked duplicity 0.6.18-0ubuntu3.1
2013-01-23 18:55:26 status half-configured duplicity 0.6.18-0ubuntu3.1
2013-01-23 18:55:26 status installed duplicity 0.6.18-0ubuntu3.1
2013-01-23 18:55:26 configure firefox 18.0.1+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:26 status unpacked firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:26 status unpacked firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:26 status unpacked firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:26 status unpacked firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:26 status unpacked firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status half-configured firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status installed firefox 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 configure firefox-globalmenu 18.0.1+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:27 status unpacked firefox-globalmenu 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status half-configured firefox-globalmenu 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status installed firefox-globalmenu 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 configure firefox-gnome-support 18.0.1+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:27 status unpacked firefox-gnome-support 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status half-configured firefox-gnome-support 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status installed firefox-gnome-support 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 configure firefox-locale-de 18.0.1+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:27 status unpacked firefox-locale-de 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status half-configured firefox-locale-de 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 status installed firefox-locale-de 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:27 configure firefox-locale-en 18.0.1+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:27 status unpacked firefox-locale-en 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:28 status half-configured firefox-locale-en 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:28 status installed firefox-locale-en 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:28 configure firefox-locale-zh-hans 18.0.1+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:28 status unpacked firefox-locale-zh-hans 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:28 status half-configured firefox-locale-zh-hans 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:28 status installed firefox-locale-zh-hans 18.0.1+build1-0ubuntu0.12.04.1
2013-01-23 18:55:28 configure gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.2 <none>
2013-01-23 18:55:28 status unpacked gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:28 status half-configured gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:28 status installed gir1.2-networkmanager-1.0 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:28 configure gnome-control-center-data 1:3.4.2-0ubuntu0.8 <none>
2013-01-23 18:55:28 status unpacked gnome-control-center-data 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:28 status unpacked gnome-control-center-data 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:28 status unpacked gnome-control-center-data 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:28 status half-configured gnome-control-center-data 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:28 status installed gnome-control-center-data 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:29 configure gnome-control-center 1:3.4.2-0ubuntu0.8 <none>
2013-01-23 18:55:29 status unpacked gnome-control-center 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:29 status half-configured gnome-control-center 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:29 status installed gnome-control-center 1:3.4.2-0ubuntu0.8
2013-01-23 18:55:29 configure gnome-games-data 1:3.4.1-0ubuntu2.2 <none>
2013-01-23 18:55:29 status unpacked gnome-games-data 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 status half-configured gnome-games-data 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 status installed gnome-games-data 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 configure gnomine 1:3.4.1-0ubuntu2.2 <none>
2013-01-23 18:55:29 status unpacked gnomine 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 status half-configured gnomine 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 status installed gnomine 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 configure mahjongg 1:3.4.1-0ubuntu2.2 <none>
2013-01-23 18:55:29 status unpacked mahjongg 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 status half-configured mahjongg 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 status installed mahjongg 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 configure gnome-sudoku 1:3.4.1-0ubuntu2.2 <none>
2013-01-23 18:55:29 status unpacked gnome-sudoku 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:29 status half-configured gnome-sudoku 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:30 status installed gnome-sudoku 1:3.4.1-0ubuntu2.2
2013-01-23 18:55:30 configure grub-common 1.99-21ubuntu3.7 <none>
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status unpacked grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:30 status half-configured grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:31 status installed grub-common 1.99-21ubuntu3.7
2013-01-23 18:55:31 configure grub2-common 1.99-21ubuntu3.7 <none>
2013-01-23 18:55:31 status unpacked grub2-common 1.99-21ubuntu3.7
2013-01-23 18:55:31 status half-configured grub2-common 1.99-21ubuntu3.7
2013-01-23 18:55:31 status installed grub2-common 1.99-21ubuntu3.7
2013-01-23 18:55:31 configure grub-pc-bin 1.99-21ubuntu3.7 <none>
2013-01-23 18:55:31 status unpacked grub-pc-bin 1.99-21ubuntu3.7
2013-01-23 18:55:31 status half-configured grub-pc-bin 1.99-21ubuntu3.7
2013-01-23 18:55:31 status installed grub-pc-bin 1.99-21ubuntu3.7
2013-01-23 18:55:31 configure grub-pc 1.99-21ubuntu3.7 <none>
2013-01-23 18:55:31 status unpacked grub-pc 1.99-21ubuntu3.7
2013-01-23 18:55:31 status unpacked grub-pc 1.99-21ubuntu3.7
2013-01-23 18:55:31 status unpacked grub-pc 1.99-21ubuntu3.7
2013-01-23 18:55:31 status half-configured grub-pc 1.99-21ubuntu3.7
2013-01-23 18:55:42 status installed grub-pc 1.99-21ubuntu3.7
2013-01-23 18:55:42 configure libnautilus-extension1a 1:3.4.2-0ubuntu6 <none>
2013-01-23 18:55:42 status unpacked libnautilus-extension1a 1:3.4.2-0ubuntu6
2013-01-23 18:55:42 status half-configured libnautilus-extension1a 1:3.4.2-0ubuntu6
2013-01-23 18:55:42 status installed libnautilus-extension1a 1:3.4.2-0ubuntu6
2013-01-23 18:55:42 configure libnm-glib-vpn1 0.9.4.0-0ubuntu4.2 <none>
2013-01-23 18:55:42 status unpacked libnm-glib-vpn1 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:42 status half-configured libnm-glib-vpn1 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:42 status installed libnm-glib-vpn1 0.9.4.0-0ubuntu4.2
2013-01-23 18:55:42 configure vlc-data 2.0.5-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:42 status unpacked vlc-data 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:42 status unpacked vlc-data 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:42 status unpacked vlc-data 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status half-configured vlc-data 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status installed vlc-data 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 configure libvlccore5 2.0.5-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:43 status unpacked libvlccore5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status half-configured libvlccore5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status installed libvlccore5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 configure libvlc5 2.0.5-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:43 status unpacked libvlc5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status half-configured libvlc5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status installed libvlc5 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 configure vlc-nox 2.0.5-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:43 status unpacked vlc-nox 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status half-configured vlc-nox 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 status installed vlc-nox 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:43 configure vlc-plugin-notify 2.0.5-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:43 status unpacked vlc-plugin-notify 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 status half-configured vlc-plugin-notify 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 status installed vlc-plugin-notify 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 configure vlc-plugin-pulse 2.0.5-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:44 status unpacked vlc-plugin-pulse 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 status half-configured vlc-plugin-pulse 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 status installed vlc-plugin-pulse 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 configure vlc 2.0.5-0ubuntu0.12.04.1 <none>
2013-01-23 18:55:44 status unpacked vlc 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 status half-configured vlc 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 status installed vlc 2.0.5-0ubuntu0.12.04.1
2013-01-23 18:55:44 configure linux-image-generic-pae 3.2.0.36.43 <none>
2013-01-23 18:55:44 status unpacked linux-image-generic-pae 3.2.0.36.43
2013-01-23 18:55:44 status half-configured linux-image-generic-pae 3.2.0.36.43
2013-01-23 18:55:44 status installed linux-image-generic-pae 3.2.0.36.43
2013-01-23 18:55:44 configure linux-headers-3.2.0-36 3.2.0-36.57 <none>
2013-01-23 18:55:44 status unpacked linux-headers-3.2.0-36 3.2.0-36.57
2013-01-23 18:55:44 status half-configured linux-headers-3.2.0-36 3.2.0-36.57
2013-01-23 18:55:44 status installed linux-headers-3.2.0-36 3.2.0-36.57
2013-01-23 18:55:44 configure linux-headers-3.2.0-36-generic-pae 3.2.0-36.57 <none>
2013-01-23 18:55:44 status unpacked linux-headers-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:55:45 status half-configured linux-headers-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:55:46 status installed linux-headers-3.2.0-36-generic-pae 3.2.0-36.57
2013-01-23 18:55:46 configure linux-headers-generic-pae 3.2.0.36.43 <none>
2013-01-23 18:55:46 status unpacked linux-headers-generic-pae 3.2.0.36.43
2013-01-23 18:55:46 status half-configured linux-headers-generic-pae 3.2.0.36.43
2013-01-23 18:55:46 status installed linux-headers-generic-pae 3.2.0.36.43
2013-01-23 18:55:46 configure linux-generic-pae 3.2.0.36.43 <none>
2013-01-23 18:55:46 status unpacked linux-generic-pae 3.2.0.36.43
2013-01-23 18:55:46 status half-configured linux-generic-pae 3.2.0.36.43
2013-01-23 18:55:46 status installed linux-generic-pae 3.2.0.36.43
2013-01-23 18:55:46 configure linux-libc-dev 3.2.0-36.57 <none>
2013-01-23 18:55:46 status unpacked linux-libc-dev 3.2.0-36.57
2013-01-23 18:55:46 status half-configured linux-libc-dev 3.2.0-36.57
2013-01-23 18:55:46 status installed linux-libc-dev 3.2.0-36.57
2013-01-23 18:55:46 configure nautilus-data 1:3.4.2-0ubuntu6 <none>
2013-01-23 18:55:46 status unpacked nautilus-data 1:3.4.2-0ubuntu6
2013-01-23 18:55:46 status half-configured nautilus-data 1:3.4.2-0ubuntu6
2013-01-23 18:55:47 status installed nautilus-data 1:3.4.2-0ubuntu6
2013-01-23 18:55:47 configure nautilus 1:3.4.2-0ubuntu6 <none>
2013-01-23 18:55:47 status unpacked nautilus 1:3.4.2-0ubuntu6
2013-01-23 18:55:47 status unpacked nautilus 1:3.4.2-0ubuntu6
2013-01-23 18:55:47 status half-configured nautilus 1:3.4.2-0ubuntu6
2013-01-23 18:55:47 status installed nautilus 1:3.4.2-0ubuntu6
2013-01-23 18:55:47 configure pulseaudio-utils 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:55:47 status unpacked pulseaudio-utils 1:1.1-0ubuntu15.2
2013-01-23 18:55:47 status half-configured pulseaudio-utils 1:1.1-0ubuntu15.2
2013-01-23 18:55:47 status installed pulseaudio-utils 1:1.1-0ubuntu15.2
2013-01-23 18:55:47 configure pulseaudio 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:55:47 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:47 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:47 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:47 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status unpacked pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status half-configured pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status installed pulseaudio 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 configure pulseaudio-module-gconf 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:55:48 status unpacked pulseaudio-module-gconf 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status half-configured pulseaudio-module-gconf 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status installed pulseaudio-module-gconf 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 configure pulseaudio-module-x11 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:55:48 status unpacked pulseaudio-module-x11 1:1.1-0ubuntu15.2
2013-01-23 18:55:48 status half-configured pulseaudio-module-x11 1:1.1-0ubuntu15.2
2013-01-23 18:55:49 status installed pulseaudio-module-x11 1:1.1-0ubuntu15.2
2013-01-23 18:55:49 configure software-center 5.2.7 <none>
2013-01-23 18:55:49 status unpacked software-center 5.2.7
2013-01-23 18:55:49 status unpacked software-center 5.2.7
2013-01-23 18:55:49 status half-configured software-center 5.2.7
2013-01-23 18:56:19 status installed software-center 5.2.7
2013-01-23 18:56:19 configure steam 1.0.0.22 <none>
2013-01-23 18:56:19 status unpacked steam 1.0.0.22
2013-01-23 18:56:19 status unpacked steam 1.0.0.22
2013-01-23 18:56:19 status half-configured steam 1.0.0.22
2013-01-23 18:56:19 status installed steam 1.0.0.22
2013-01-23 18:56:19 configure thunderbird 17.0.2+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:56:19 status unpacked thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:19 status unpacked thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:19 status unpacked thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 status unpacked thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 status half-configured thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 status installed thunderbird 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 configure thunderbird-globalmenu 17.0.2+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:56:20 status unpacked thunderbird-globalmenu 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 status half-configured thunderbird-globalmenu 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 status installed thunderbird-globalmenu 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 configure thunderbird-gnome-support 17.0.2+build1-0ubuntu0.12.04.1 <none>
2013-01-23 18:56:20 status unpacked thunderbird-gnome-support 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 status half-configured thunderbird-gnome-support 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 status installed thunderbird-gnome-support 17.0.2+build1-0ubuntu0.12.04.1
2013-01-23 18:56:20 configure unattended-upgrades 0.76ubuntu1 <none>
2013-01-23 18:56:20 status unpacked unattended-upgrades 0.76ubuntu1
2013-01-23 18:56:20 status unpacked unattended-upgrades 0.76ubuntu1
2013-01-23 18:56:20 status unpacked unattended-upgrades 0.76ubuntu1
2013-01-23 18:56:20 status unpacked unattended-upgrades 0.76ubuntu1
2013-01-23 18:56:21 status unpacked unattended-upgrades 0.76ubuntu1
2013-01-23 18:56:21 status half-configured unattended-upgrades 0.76ubuntu1
2013-01-23 18:56:22 status installed unattended-upgrades 0.76ubuntu1
2013-01-23 18:56:22 configure vino 3.4.2-0ubuntu1.2 <none>
2013-01-23 18:56:22 status unpacked vino 3.4.2-0ubuntu1.2
2013-01-23 18:56:22 status unpacked vino 3.4.2-0ubuntu1.2
2013-01-23 18:56:22 status half-configured vino 3.4.2-0ubuntu1.2
2013-01-23 18:56:22 status installed vino 3.4.2-0ubuntu1.2
2013-01-23 18:56:22 configure x11-common 1:7.6+12ubuntu2 <none>
2013-01-23 18:56:22 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:22 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:22 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:22 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:22 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:22 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:22 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status unpacked x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:23 status half-configured x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:24 status installed x11-common 1:7.6+12ubuntu2
2013-01-23 18:56:24 configure x11proto-dri2-dev 2.8-1~precise1 <none>
2013-01-23 18:56:24 status unpacked x11proto-dri2-dev 2.8-1~precise1
2013-01-23 18:56:24 status half-configured x11proto-dri2-dev 2.8-1~precise1
2013-01-23 18:56:25 status installed x11proto-dri2-dev 2.8-1~precise1
2013-01-23 18:56:25 configure x11proto-gl-dev 1.4.16-1~precise1 <none>
2013-01-23 18:56:25 status unpacked x11proto-gl-dev 1.4.16-1~precise1
2013-01-23 18:56:25 status half-configured x11proto-gl-dev 1.4.16-1~precise1
2013-01-23 18:56:25 status installed x11proto-gl-dev 1.4.16-1~precise1
2013-01-23 18:56:25 configure xserver-xorg-video-all 1:7.6+12ubuntu2 <none>
2013-01-23 18:56:25 status unpacked xserver-xorg-video-all 1:7.6+12ubuntu2
2013-01-23 18:56:25 status half-configured xserver-xorg-video-all 1:7.6+12ubuntu2
2013-01-23 18:56:25 status installed xserver-xorg-video-all 1:7.6+12ubuntu2
2013-01-23 18:56:25 configure xserver-xorg-input-all 1:7.6+12ubuntu2 <none>
2013-01-23 18:56:25 status unpacked xserver-xorg-input-all 1:7.6+12ubuntu2
2013-01-23 18:56:25 status half-configured xserver-xorg-input-all 1:7.6+12ubuntu2
2013-01-23 18:56:25 status installed xserver-xorg-input-all 1:7.6+12ubuntu2
2013-01-23 18:56:25 configure xserver-xorg 1:7.6+12ubuntu2 <none>
2013-01-23 18:56:25 status unpacked xserver-xorg 1:7.6+12ubuntu2
2013-01-23 18:56:25 status half-configured xserver-xorg 1:7.6+12ubuntu2
2013-01-23 18:56:26 status installed xserver-xorg 1:7.6+12ubuntu2
2013-01-23 18:56:26 configure xorg 1:7.6+12ubuntu2 <none>
2013-01-23 18:56:26 status unpacked xorg 1:7.6+12ubuntu2
2013-01-23 18:56:26 status half-configured xorg 1:7.6+12ubuntu2
2013-01-23 18:56:26 status installed xorg 1:7.6+12ubuntu2
2013-01-23 18:56:26 configure pulseaudio-module-bluetooth 1:1.1-0ubuntu15.2 <none>
2013-01-23 18:56:26 status unpacked pulseaudio-module-bluetooth 1:1.1-0ubuntu15.2
2013-01-23 18:56:26 status half-configured pulseaudio-module-bluetooth 1:1.1-0ubuntu15.2
2013-01-23 18:56:26 status installed pulseaudio-module-bluetooth 1:1.1-0ubuntu15.2
2013-01-23 18:56:26 configure openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1 <none>
2013-01-23 18:56:26 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:27 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:28 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:28 status unpacked openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:28 status half-configured openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:28 status installed openjdk-7-jre-headless 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 configure openjdk-7-jre-lib 7u9-2.3.4-0ubuntu1.12.04.1 <none>
2013-01-23 18:56:29 status unpacked openjdk-7-jre-lib 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status half-configured openjdk-7-jre-lib 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status installed openjdk-7-jre-lib 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 configure openjdk-7-jre 7u9-2.3.4-0ubuntu1.12.04.1 <none>
2013-01-23 18:56:29 status unpacked openjdk-7-jre 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status half-configured openjdk-7-jre 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status installed openjdk-7-jre 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 configure icedtea-7-jre-cacao 7u9-2.3.4-0ubuntu1.12.04.1 <none>
2013-01-23 18:56:29 status unpacked icedtea-7-jre-cacao 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status half-configured icedtea-7-jre-cacao 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status installed icedtea-7-jre-cacao 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 configure icedtea-7-jre-jamvm 7u9-2.3.4-0ubuntu1.12.04.1 <none>
2013-01-23 18:56:29 status unpacked icedtea-7-jre-jamvm 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status half-configured icedtea-7-jre-jamvm 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 status installed icedtea-7-jre-jamvm 7u9-2.3.4-0ubuntu1.12.04.1
2013-01-23 18:56:29 trigproc libc-bin 2.15-0ubuntu10.3 <none>
2013-01-23 18:56:29 status half-configured libc-bin 2.15-0ubuntu10.3
2013-01-23 18:56:30 status installed libc-bin 2.15-0ubuntu10.3
```

---

### Post by argoz17 on 2013-01-24
I do get an internal error report...but I am not sure what to do with it besides submitting it

---

### Post by kostkon on 2013-01-25
> **argoz17 said:**
> I do get an internal error report...but I am not sure what to do with it besides submitting it
What kind of error and where?

Hmm, I can see from the log that gnome-menus was updated. If you open its simple editor, e.g. in a terminal or ALT+F2 and give:
```
gmenu-simple-editor
```
do you see your menus and menu items listed there?

You could try reinstalling it, for example:
```
sudo apt-get clean && sudo apt-get install gnome-menus --reinstall
```
Also, you could check your xsession-errors file for any related error messages. You might need to use the search feature of your text editor because that file is usually long.
```
gedit ~/.xsession-errors
```

Hope that helps.

---

### Post by furything on 2013-01-25
I have had this before (admittedly with xfce not unity).

For me I deleted but suggest you rename your menu configuration file from you home directory '.config/menus/applications.menu' and reboot

The system rebuilds the default list I believe from somewhere in /usr/share (of course if you find this file you could just copy it over)

---

### Post by argoz17 on 2013-01-27
Any chance I could get step by step instructions how to do this or a link to instructions?
Thank you very much

---

### Post by furything on 2013-01-30
Sorry only just looked back on thread and assuming you meant me. HAve you sorted this yet?

xfce is different with the menu struture so don't think will work for you.

However
Through the file manger make sure hidden files are visible (through menu items and dependent upon which one you use). In your home directory you should now see .config inside there a sub folder menus. Suggest you post them here and I can compare to mine.
What they should do is point back to a main os file. 
Again from the directory it tells you - post the menu files and I will see if they are correct.

---

### Post by argoz17 on 2013-02-11
So I went to Home>.config>menus
-Inside of 'menus' is a folder called 'applications-merged' and a file called 'applications.menu'
-applications-merged folder is empty.
-I opened 'applications.menu' and this is what was in it. 
-<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

---

### Post by argoz17 on 2013-02-11
So what I found was Home>.config>menus
-Under 'menus' is a folder called 'applications-merged' and a document called 'applications.menu'
-the 'applications-merged' folder is empty
-When I opened 'applications.menu' I found this:

<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
</Menu>

---

### Post by dcommini on 2013-04-29
Try this...

> **UnknownFearNG said:**
> Sorry I haven't replied in awhile, but I have the solution. Looking at an AskUbuntu question regarding this situation, [Dash search gives no results]("http://askubuntu.com/questions/125843/dash-search-gives-no-result"), the second reply has the solution that you need. It worked for me as well. What you need to do is run:

```

rm ~/.cache/software-center -R
unity --reset &

```

After they both are done running, do a restart and everything should be back to normal. (from this [thread]("http://ubuntuforums.org/newreply.php?do=newreply&p=12295601"))

I was having the same problem and this worked for me.

---

