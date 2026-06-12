---
title: "Problem with RealVNC viewer"
date: 2017-08-07
forum: General Help
---

### Post by xuraax on 2017-08-07
Hi, I have downloaded the latest version of this application and manually installed the program by creating the .desktop file to run from GUI on 2 computers running Ubuntu 16.04. The intention is to run a raspberry pi headless.

On one system the program runs normally either from the GUI or from the terminal by typing ./VNC........etc.

On the second system  the Viewer starts but does not connect using either of the above methods. However I am able to run normally from terminal if I do  sudo ./VNC........etc. How can I run the viewer from GUI?

---

### Post by vocx on 2017-08-07
> **xuraax said:**
> Hi, I have downloaded the latest version of this application and manually installed the program by creating the .desktop file to run from GUI on 2 computers running Ubuntu 16.04. The intention is to run a raspberry pi headless.

On one system the program runs normally either from the GUI or from the terminal by typing ./VNC........etc.

On the second system  the Viewer starts but does not connect using either of the above methods. However I am able to run normally from terminal if I do  sudo ./VNC........etc. How can I run the viewer from GUI?
Where did you put the executable?

In Ubuntu systems a "bin" folder under your home folder is added automatically to the PATH variable, so you may want to put your executable there.
```

mkdir -p $HOME/bin
mv -t $HOME/bin VNC-Viewer-6.0.0-Linux-x64

```

Where did you put your desktop file? The desktop files, when installed by the package manager or "apt", are usually in "/usr/share/applications". However, you don't want to touch this folder.

Since you are creating a desktop file yourself, you should put it under your home folder as well.
```

mv -t $HOME/.local/share/applications VNC-Viewer.desktop

```

You should not need "sudo" to run the application. If you need "sudo", that means that while creating the desktop file the permissions were not correct. Maybe the permissions are not correct either in the executable itself. You should confirm the ownership and permission of the files.
```

chown xuraax:xuraax $HOME/.local/share/applications VNC-Viewer.desktop
chown xuraax:xuraax $HOME/bin/VNC-Viewer-6.0.0-Linux-x64
chmod ugo+rwx $HOME/bin/VNC-Viewer-6.0.0-Linux-x64

```

Don't use "sudo" indiscriminately, it can give your more problems if you accidentally change the permissions of certain files. Better learn about Linux permissions properly. Only use "sudo" when you really want to modify system files, not when operating on your own files.

---

### Post by xuraax on 2017-08-08
Thank you for your fast reply.

> **vocx said:**
> Where did you put the executable?



The executable is in the home directory on both systems.

> 

In Ubuntu systems a "bin" folder under your home folder is added automatically to the PATH variable, so you may want to put your executable there.



I am no expert in linux but I conclude that since the program does start to run ( it just does not connect) this may not be the problem. Also there is no "bin" folder on both systems.

> 

Where did you put your desktop file? The desktop files, when installed by the package manager or "apt", are usually in "/usr/share/applications". However, you don't want to touch this folder.

Since you are creating a desktop file yourself, you should put it under your home folder as well.



I have put the .desktop file in both the /usr/share/applications directory and in the /HOME/Desktop directory. In any case I believe the .desktop file is not used when you run the application from a terminal.

> 

You should not need "sudo" to run the application. If you need "sudo", that means that while creating the desktop file the permissions were not correct. Maybe the permissions are not correct either in the executable itself. You should confirm the ownership and permission of the files.



The permissions for the application file and the .desktop file in the ~/Desktop directory is 775 and for the .desktop file in /.../applications/ directory is 644 on both systems

> 

Don't use "sudo" indiscriminately, it can give your more problems if you accidentally change the permissions of certain files. Better learn about Linux permissions properly. Only use "sudo" when you really want to modify system files, not when operating on your own files.

Agreed but sometimes you have to.

---

### Post by vocx on 2017-08-08
> **xuraax said:**
> Thank you for your fast reply.

I am no expert in linux but I conclude that since the program does start to run ( it just does not connect) this may not be the problem. Also there is no "bin" folder on both systems.

Correct. And this is why in my previous post I suggested you create the directory and copy the executable there. In this way, you have your things organized.

> 
I have put the .desktop file in both the /usr/share/applications directory and in the /HOME/Desktop directory. In any case I believe the .desktop file is not used when you run the application from a terminal.

As I said, everything that you do with your personal files should be done in your home folder. So, it is better if you move the .dekstop file into the "$HOME/.local" folder I mentioned in my previous post.

> 
The permissions for the application file and the .desktop file in the ~/Desktop directory is 775 and for the .desktop file in /.../applications/ directory is 644 on both systems

But what is the ownership? You have to own the files as well. If you used sudo to create the files, it is possible the files are owned by "root" and not your user. In my previous post, I also mentioned to change the ownership of the files with "chown".

> 
Agreed but sometimes you have to.
You have to use "sudo" if you are going to do system level operations like updating and upgrading your system. For creating what is essentially a shortcut, you don't need to use "sudo", as long as you put the file in your home directory.

---

### Post by xuraax on 2017-08-09
> **vocx said:**
> 


But what is the ownership? You have to own the files as well. If you used sudo to create the files, it is possible the files are owned by "root" and not your user. In my previous post, I also mentioned to change the ownership of the files with "chown".




OOPS!!! I thought ownership and permissions are one and the same thing. I need to read up on the topic before I change anything. Will get back. Thanks for now.

---

### Post by vocx on 2017-08-09
> **xuraax said:**
> OOPS!!! I thought ownership and permissions are one and the same thing. I need to read up on the topic before I change anything. Will get back. Thanks for now.

The syntax is
```

chown user:group file

```
For your regular user, the group should be the same as the user, so it would be something like
```

chown xuraax:xuraax file

```

You can check your group with the command "id".

In my first post I wrote that you could change ownership with "chown". It's like nobody reads my posts :'(
> **vocx said:**
> ...
You should not need "sudo" to run the application. If you need "sudo", that means that while creating the desktop file the permissions were not correct. Maybe the permissions are not correct either in the executable itself. You should confirm the ownership and permission of the files.
```

chown xuraax:xuraax $HOME/.local/share/applications VNC-Viewer.desktop
chown xuraax:xuraax $HOME/bin/VNC-Viewer-6.0.0-Linux-x64
chmod ugo+rwx $HOME/bin/VNC-Viewer-6.0.0-Linux-x64

```...

---

### Post by xuraax on 2017-08-09
> **vocx said:**
> The syntax is
```

chown user:group file

```
For your regular user, the group should be the same as the user, so it would be something like
```

chown xuraax:xuraax file

```

[QUOTE]

You can check your group with the command "id".

In my first post I wrote that you could change ownership with "chown". It's like nobody reads my posts :



On both systems the ownership is the same of the form "xuraax:xuraax" for both the application file and the .desktop file in the ~/Desktop folder.

The ownership for the .desktop file in the /usr....../applications/ folder is root:root in both systems. I need to add that the ownership and permissions for other working programs in these folders is exactly the same.

Also the result of the id command is practically the same except for 2 numbers as follows:

on the working system it is:

uid=1000(xuraax) gid=1000(joee3) groups=1000(xuraax),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),115(lpadmin),131(sambashare)

on the system where I have issues it is:

uid=1000(xuraax) gid=1000(joee3) groups=1000(xuraax),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)

I have no clue what these numbers mean.

---

### Post by vocx on 2017-08-09
> **xuraax said:**
> 
on the working system it is:
```

uid=1000(xuraax) gid=1000(joee3) groups=1000(xuraax),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),115(lpadmin),131(sambashare)

```

on the system where I have issues it is:
```

uid=1000(xuraax) gid=1000(joee3) groups=1000(xuraax),4(adm),24(cdrom),27(sudo),30(dip),46(plugdev),113(lpadmin),128(sambashare)

```
I have no clue what these numbers mean.

The id number is just that, an identification number differentiating different users and groups. One user has a unique "id", which is normally 1000. A second user may have 1001, and the next one 1002, and so on. A group allows setting permissions for all the members of the group. Again, a group id 1000 is the default for your user. Additionally, it says that you are part of several groups, with their respective ids. If your user were not part of the "sudo" group, you wouldn't be able to use "sudo". If your user were not part of "sambashare" group, you wouldn't be able to share samba directories, etc. Everything is setup for your when you install these components so for the most part you don't need to worry.

I find it a bit odd that your group id is 1000 but says joee3. It should say xuraax. Or maybe you are changing the information here in the forum. Anyway, you need to be sure the files you want to execute are owned by you, and have the correct executable permissions, as I mentioned in the first post.
```

chown xuraax:joee3 file
chmod ugo+rwx file

```

---

### Post by xuraax on 2017-08-10
> **vocx said:**
> 

I find it a bit odd that your group id is 1000 but says joee3. It should say xuraax. Or maybe you are changing the information here in the forum. Anyway, you need to be sure the files you want to execute are owned by you, and have the correct executable permissions, as I mentioned in the first post.



Sorry about that. The actual ownership is joee3:joee3 but I tried to change this in the mail to xuraax. I failed to change all instances.

Getting back to the original problem, the fact that Viewer starts in GUI and projects the initial main screen properly but only fails when a subsequent  screen comes up when I press "connect" leads me to think that there is basically nothing wrong with the original permissions and ownership of the program.

I think that when I am pressing "connect", Viewer is trying to call up a service, which on this computer requires different permissions. The question is which services.

---

### Post by vocx on 2017-08-10
> **xuraax said:**
> Sorry about that. The actual ownership is joee3:joee3 but I tried to change this in the mail to xuraax. I failed to change all instances.

Getting back to the original problem, the fact that Viewer starts in GUI and projects the initial main screen properly but only fails when a subsequent  screen comes up when I press "connect" leads me to think that there is basically nothing wrong with the original permissions and ownership of the program.

I think that when I am pressing "connect", Viewer is trying to call up a service, which on this computer requires different permissions. The question is which services.
The thing is this, sometimes programs need to write temporary files to store the preferences of the program. If you ran "sudo VNC_viewer" once, maybe it wrote come configuration files under your $HOME directory. Since the program was run with "sudo" these files may now be owned by "root", and you may not be able to overwrite them when you start the program again with your normal user. I'm not sure if this happened, but it could be a cause. Thus why I stress to not run things with "sudo" if you don't need to. You should give normal permissions to your user and own that file so that you don't have these problems.

---

### Post by xuraax on 2017-08-11
> **vocx said:**
> The thing is this, sometimes programs need to write temporary files to store the preferences of the program. If you ran "sudo VNC_viewer" once, maybe it wrote come configuration files under your $HOME directory. Since the program was run with "sudo" these files may now be owned by "root", and you may not be able to overwrite them when you start the program again with your normal user. I'm not sure if this happened, but it could be a cause. Thus why I stress to not run things with "sudo" if you don't need to. You should give normal permissions to your user and own that file so that you don't have these problems.

Good point. 

I am sure I first ran the program without sudo. However the program does create its own .VNC directory with some files in it so I will delete this and see what happens when it creates it again.

---

