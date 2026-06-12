---
title: "XFCE + FreeNX"
date: 2006-07-26
forum: General Help
---

### Post by skuzzy_ on 2006-07-26
Alright, the session fails to start for me.  After authentication is complete when I have Run command: "startxfce4" and Floating Window or New Virtual Desktop it outputs

NX> 105 NX> 504 Session startup failed.
NX> 1004 Error: nxagent failed to start with: Unrecognized option: 1
NX> 1001 Bye.
Killed by signal 15. 

I haven't even gotten to renaming the display_plugin file to fix the resolution :p

Any help would be appreciated, thanks.

---

### Post by skuzzy_ on 2006-07-26
After messing with it since this post
I have done nxserver --adduser <user> and nxserver --passwd <user> despite documentation stating that it wasn't necessary.  I have PublicKeysAllowed yes
AuthorizedKeysFile /var/lib/nxserver/home/.ssh/authorized_keys2
                   (also &h/.ssh/authorized_keys2)
AllowUsers nx

have also tried other variations... and even though I psftp'd the client.id_dsa.key and have imported it into my NX Client (Windows and also version 2.0) (also not a custom key therefore it was default) it is saying

Server not installed or NX access disabled.

I have done nxserver --status and well as ssh status and both are running and despite this the error is still present.  I have also made sure the nx user was unlocked with passwd -u nx.

---

### Post by rick_1010 on 2006-09-12
I've been having exactly the same problem and its driving me crazy, I've searched every thread I could find on these forums and Google about the topic and nothing that I have tried works. So far the only distro I have been succesful at getting FreeNX to work with is Fedora and I really need to switch to Ubuntu, preferrably Xubuntu as I'm building an OpenMosix cluster with low end machines.. anyways, I am able to connect but I still keep getting the "Killed by signal 15" error message.

I am using the newest version of the NX client to connect, it seems that the packages available for Ubuntu of FreeNX are an older version than are available for in RPM, I am wondering if this has something to do with it.. do I have to use a 1.5 client to connect? If so could anyone point me to where I can download the older client (for both Linux and Windows) as they are not listed on the NoMachine site.

Any help would be appreciated.

---

### Post by rick_1010 on 2006-09-13
This thread is still open: [http://www.ubuntuforums.org/showthread.php?t=241651&highlight=install+freenx+ubuntu](http://www.ubuntuforums.org/showthread.php?t=241651&highlight=install+freenx+ubuntu) and deals with the same issue I believe but for all Ubuntu distros, I think this has to do with the sshd_config from what I can tell.. as I just ran a manual install and was given this message, if anyone knows where sshd_config is so it can be edited I think this would solve the problem (I am going to do a search on my system to see if I can find it)

---

### Post by marcelinoM on 2006-09-14
This won't help you much but I ran into the same problem and just completed these steps with the user account I was logging in with and it worked fine.

(steps from here [http://www.ubuntuforums.org/showthread.php?t=241651&highlight=install+freenx+ubuntu](http://www.ubuntuforums.org/showthread.php?t=241651&highlight=install+freenx+ubuntu))

Installed freenx for repos listed on that posting.

My NXserver is Ubuntu 6.06 and the NXclient is Ubuntu 6.06 Laptop.  Running GNOME on both...selected gdm during Wizard setup.

13. nxserver --adduser <remoteuser>
14. nxserver --passwd <remoteuser>
15. test the setup locally by running the client
/usr/NX/bin/nxclient

Copied client.id_dsa.key from server to laptop

16. It should bring up a client wizard.
Name the session, enter the IP of the server. Hit the configure button.
On the first tab, select Key and then import. The key is here: /var/lib/nxserver/home/.ssh/client.id_dsa.key

I installed the NXserver with this command:

apt-get install freenx nxdesktop nxviewer expectk smbfs esound-clients 

Marcelino

---

