---
title: "Can't Browse Windows Network"
date: 2006-11-13
forum: General Help
---

### Post by danfluidmind on 2006-11-13
When using "Places->Network Servers" to browse the network, after clicking on  the "Windows Network" icon, I can see the various work groups and domains, but when I double click on any of them, I just get

   Couldn't display "smb://workgroup"
   The location is not a folder

What's up with that? Do I need to install something else in order to browse Windows servers? I'm running a fairly default Edgy installation and haven't installed any extra Samba packages.

Thanks
--Dan

---

### Post by Irony on 2006-11-13
Have you enabled your windows firewall to allow home networking - for example in Norton go to firewall and auto-configure home networking.

---

### Post by mauserrifle on 2006-11-13
I have the same issue.
Hit F5 on your keyboard when the window is active. The blank icon will probably change into a ubuntu icon and you can acces it

Hope this helps

---

### Post by danfluidmind on 2006-11-13
> **Irony said:**
> Have you enabled your windows firewall to allow home networking - for example in Norton go to firewall and auto-configure home networking.

This isn't a little home windows machine. These are several windows file servers at an office. The Windows and Mac desktops can browse the network without a problem.

> **mauserrifle said:**
> I have the same issue.
Hit F5 on your keyboard when the window is active. The blank icon will probably change into a ubuntu icon and you can acces it

Okay, I hit F5 and it crashed the File Browser. But then when I went to start browsing again, the domain now had a nice icon and I was able to open it and see the servers in it! Thanks a lot.

So, what the hell is that "hit F5" all about? How is anyone suppose to know to do that? (How did YOU find that out?) And, more importantly, WHY do we need to do that at all?

--Dan

---

### Post by mauserrifle on 2006-11-14
I couldn't acces my other windows pc in my house. It had no icon.
So i hit f5 just to try and voila. It fixed it.
I must do this at WORKGROUP. PCNAME

Anybody know if this is a bug? apperently i'm not the only one

---

### Post by paperdiesel on 2006-11-14
Hitting F5 is not a bug.  F5 is just a shortcut key for "refresh" -- most internet and file system browsers use F5 to refresh the page/directory (look at the menu, you'll see something like "reload" or "refresh" and the F5 shortcut indicator).  When you're hitting F5, you're telling your system to update its information on the network shares.  At that point, it correctly detects the network shares and knows how to talk to them.

One thing that people fail to understand about samba sharing is that it's not "immediately on" at first.  When you enable sharing or initially bring your computer up on a network, it will take a while (sometimes up to a couple of minutes or more) before that computer can successfully see and connect to the other shares.

Be patient.  Refresh often.

---

### Post by danfluidmind on 2006-11-14
Thanks.

Okay, I can see why the F5 key did something. But there still seems to be a serious problem here. It's not just that it's taking a long time for Samba to recognize the domains/workgroups/servers. My machine's been on for weeks now and I've openned "Places->Network Servers" many times. It should have recognized them by now.

It's not that the domains, workgroups and servers don't show up. It's that they show up as blank icons that are unrecognizable as domains/workgroups/servers by the File Browser.

Here's the strange part. Hitting F5 (or CTRL-R, or clicking the Reload button) is erratic. If I reload once, some of the icons might become active while others don't. Then if I reload again, ones that were active suddenly become inactive and others become active. Each time I reload, all the icons change. There definitely seems to be a bug here.

I'm running Ubuntu 6.10, Samba is 3.0.22-1ubuntu4, Nautilis 2.16.1-0ubuntu3

--Dan

---

### Post by dbott67 on 2006-11-14
A few things to verify:
1. Make sure you have samba, smbfs and smbclient installed

Run the command smbtree and post the output here:
```
dbott@thedrake:~$ smbtree
Password:
MSHOME
        \\THEDRAKE                      thedrake server (Samba, Ubuntu)
                \\THEDRAKE\print$               Printer Drivers
                \\THEDRAKE\dbott-P4
                \\THEDRAKE\IPC$                 IPC Service (thedrake server (Samba, Ubuntu))
                \\THEDRAKE\ADMIN$               IPC Service (thedrake server (Samba, Ubuntu))
        \\DAPPER                        dapper server (Samba, Ubuntu)
                \\DAPPER\print$                 Printer Drivers
                \\DAPPER\ndis
                \\DAPPER\IPC$                   IPC Service (dapper server (Samba, Ubuntu))
                \\DAPPER\ADMIN$                 IPC Service (dapper server (Samba, Ubuntu))

```

Also, some issues arise because of the way SMB shares "announce" themselves to the network.  Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail.  Windows uses WINS service to allow users to browse by computer name (also known in Windows-speak as Netbios name).  WINS binds the computer name to the IP address.  For the most part, this has been superceded by DNS, which binds the fully-qualified domain name to the IP address. The problem is that DNS resolution requires that:

a) You're running a DNS server
b) Each client is registered in the DNS server

The problem here is that most people don't run their own DNS server and if you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed.

There is a package in the repositories called 'winbind' that will allow you to browse by computer name.

This info is provided by 'featherking' from [this thread]("http://www.ubuntuforums.org/showthread.php?t=288022"): 

```
sudo gedit /etc/nsswitch.conf
```

find this line (it may not be exactly that)

```
hosts:          files dns mdns
```

and add wins, so now it looks like

```
hosts:          files dns mdns wins
```

then install winbind
```

sudo apt-get install winbind
```

Now trying connecting to "Places->Network Servers".

-Dave

---

### Post by danfluidmind on 2006-11-15
Thanks a lot for that response, Dave.

> **dbott67 said:**
> A few things to verify:
1. Make sure you have samba, smbfs and smbclient installed


Check


> **dbott67 said:**
> Run the command smbtree and post the output here:

Here it is. (I've taken out the volume names to make it shorter. This is just the workgroups/domains and server names:

```

WORKGROUP
        \\MACSERVER                     Mac OS X Server
        \\FEDEX          
        \\CONVERT                       Mac OS X

POWERCREATIVE
        \\WINDOWSMULE                   Windows server for miscellaneous tasks
        \\WINDOWSDEV                    Windows Development Server
        \\WIN2000TEST                   Windows 2000 Test VM
        \\POWERVAULT     
        \\LOUFS2         
        \\LOUEX2         
        \\LOUBU1         
        \\HP             
        \\LINUXDEV                      linuxdev server (Samba, Ubuntu)
        \\3DBOXX-W8206
        \\LINUXTEST                     linuxtest desktop (Samba, Ubuntu)
        \\ZX10PC         
        \\917L581   

```

> **dbott67 said:**
> Also, some issues arise because of the way SMB shares "announce" themselves to the network.  Generally, connecting via IP address works properly, but browsing by 'computer name' can occasionally fail.
...
If you have any Windows computers on the network (or Samba shares), you really should have a WINS server or 'winbind' installed.

Again, I don't think this is an issue of not having the right software installed. I went again and installed winbind as you described to see if that helped and it didn't change anything. (And if winbind were essential to make Ubuntu work correctly with Windows networks, shouldn't it be installed by default?)

The problem isn't that the windows servers (and their names) are not being seen. The problem is that File Browser seems to have a problem deciding whether to allow access to them or not. It seems to be completely arbitrary and erratic. I'll open the Browse Network window and maybe one or two of the workgroups/domains will be working properly. Then I'll refresh the window and those same workgroups will stop working and others that had not been working will start working. The same occurs with servers when I open one of the workgroups (when it happens to work). This smells awfully like a bug to me.

Here are a few screen shots of the contents of the File Browser Windows right after I select "Places->Network Servers". Each one was taken after I hit F5 to do a reload:

[IMG]http://www.poweractive.com/filebrowserproblem/WindowsNetwork_1.png[/IMG]

[IMG]http://www.poweractive.com/filebrowserproblem/WindowsNetwork_2.png[/IMG]

[IMG]http://www.poweractive.com/filebrowserproblem/WindowsNetwork_3.png[/IMG]

[IMG]http://www.poweractive.com/filebrowserproblem/WindowsNetwork_4.png[/IMG]

Something just seems to be wrong there. When I double click on the WORKGROUP icon when it's blank, I get the following error:

   Couldn't display "smb://workgroup".
   The location is not a folder.

But when I double click on it when it has the proper network icon then it shows me a list of the servers in that workgroup. But once again, some of the servers have blank icons and give that error, while others have the proper network icon and I can open them and connect. And when I hit F5 to reload, that changes in a completely random way.

Am I the only person having this problem? :-)

Thanks again.
--Dan

---

### Post by dbott67 on 2006-11-15
Hi Dan,

You're definitely not the only one experiencing this.  There's at least 3 other threads that I've posted in with similar problems:

[http://www.ubuntuforums.org/showthread.php?t=299855](http://www.ubuntuforums.org/showthread.php?t=299855)
[http://www.ubuntuforums.org/showthread.php?t=299386](http://www.ubuntuforums.org/showthread.php?t=299386)
[http://www.ubuntuforums.org/showthread.php?t=278992](http://www.ubuntuforums.org/showthread.php?t=278992)

Perhaps it is a bug in Nautilus.  Perhaps you can install 'LinNeighborhood' which is a graphic browser for SMB shares.  There's another browser as well that escapes me at the moments... I'll post it when my brain returns.

See this thread for some details:
[http://www.ubuntuforums.org/showpost.php?p=1666780&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1666780&postcount=3)

-Dave

(it's back... the program is pyNeighborhood: [http://pyneighborhood.sourceforge.net/](http://pyneighborhood.sourceforge.net/).  I couldn't find it in the repos, but I'll see if the .debs are out there.)

---

### Post by koenn on 2006-11-15
I'm seeing the same. It started recently (on a Dapper system) - I kinda dismissed it as refresh or slow network issue, smb being slow at picking up signals from remote hosts, or so. 

This thread got me wondering -  i seem to remember there was a smb related update (to Dapper) recently as well so maybe it's something in the newer smb client or other smb package. 

It doesn't bother me too much (small home network, samba shares only for storage of files a don't often need, ...) so I won't investigate, but you might want to check for bug reports about recent samba updates and/or the samba versions in edgy. 

Also; if it really bugs you : the "connect to server" thingie from "Places" still seems to work, also for connecting to samba shares. Maybe that helps you out for the time being.
That also suggests the problem is remlated to the smb "browser" feauture

---

### Post by wilberfan on 2006-11-15
Here's a thread that discusses a "superior" way to mount samba shares via cifs:

[http://www.ubuntuforums.org/showthread.php?t=288534](http://www.ubuntuforums.org/showthread.php?t=288534)

---

### Post by klsmith259 on 2006-11-15
This is a bug and it has been fixed but not updated for edgy i beleive.

---

### Post by kvonb on 2006-11-15
I'm having the same problem, it's also on the liveCD so I know it's not my network as nothing else has changed other than installing Edgy on my everyday machine.

My nautilus will browse the network now, but when I run a root (sudo) nautilus I get this:

 "nautilus cannot display smb://zen"
 "please select another viewer and try again"

This also happens on the liveCD, I don't understand it, my hostnames are setup properly.

EDIT:

WORKAROUND:  Install konqueror, it works perfectly!

---

### Post by compuguy1088 on 2006-11-18
> **dbott67 said:**
> Hi Dan,

You're definitely not the only one experiencing this.  There's at least 3 other threads that I've posted in with similar problems:

[http://www.ubuntuforums.org/showthread.php?t=299855](http://www.ubuntuforums.org/showthread.php?t=299855)
[http://www.ubuntuforums.org/showthread.php?t=299386](http://www.ubuntuforums.org/showthread.php?t=299386)
[http://www.ubuntuforums.org/showthread.php?t=278992](http://www.ubuntuforums.org/showthread.php?t=278992)

Perhaps it is a bug in Nautilus.  Perhaps you can install 'LinNeighborhood' which is a graphic browser for SMB shares.  There's another browser as well that escapes me at the moments... I'll post it when my brain returns.

See this thread for some details:
[http://www.ubuntuforums.org/showpost.php?p=1666780&postcount=3](http://www.ubuntuforums.org/showpost.php?p=1666780&postcount=3)

-Dave

(it's back... the program is pyNeighborhood: [http://pyneighborhood.sourceforge.net/](http://pyneighborhood.sourceforge.net/).  I couldn't find it in the repos, but I'll see if the .debs are out there.)

Well you are in luck, I previously ran into pyNeighborhood, to browse Samba on Xubuntu, and so I built it from source, using checkinstall. Attahed to this post is the package that I made, hopefully it works.

---

### Post by moopere on 2006-11-19
I can't get it to work.  If I install smbfs (not obvious) and I manually add the names of network servers then it seems to mount shares ok, but it won't browse for some reason.

Cheers,
Craig

---

### Post by compuguy1088 on 2006-11-19
I haven't either gotten pyNeighborhood to work, it doesn't seem to want to mount any network shares. I checked there site, and there isn't much documentation about how to use it, so I'm at a loss.

---

### Post by Biker on 2006-11-19
No you are not alone, same problem here with edgy and not with dapper (dual-boot)

---

### Post by sawjew on 2006-11-23
You have to mount samba shares as root so if you start pyneighborhood as
```
gksu pyneighborhood
``` 
then it mounts without a problem.

I have read somewhere of a way to mount samba shares as a user but I can't remember where and I have never tried it.

---

### Post by hotani on 2007-12-04
I'm seeing this problem now. In Gutsy. There are shares out there, but Nautilus does not see any of them. Browsing to "smb:///" produces an empty window. There are at least 4 different workgroups at my office, none of them are displayed.

---

### Post by ghandi69_ on 2008-01-29
I also am having this problem now.

I have a public samba share on the network.

I can ping the server, I can mount the samba share, and it shows up using smbtree, but I cannt see it using the network browser.

Also, once upon restart I could browse the network, then, upon another restart, I could not, without changing any settings.

---

