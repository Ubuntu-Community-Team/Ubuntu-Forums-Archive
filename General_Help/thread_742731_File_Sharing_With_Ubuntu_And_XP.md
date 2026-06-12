---
title: "File Sharing With Ubuntu And XP"
date: 2008-04-02
forum: General Help
---

### Post by JayDeePlus on 2008-04-02
i have 3 computer and a router..........i have setup router and setup 2 XP machines to file share.........that is working right..........try to do it with ubuntu machine.........it's able to see the main xp machine through network place on ubuntu machine......but when i click on the machine it gives me an error " The Folder Contents Could Not Be displayed" is there some plugin or package i need to install to be able to speak to a windows machine?

---

### Post by Cope57 on 2008-04-02
From the UbuntuGuide
[How to install Samba Server for files/folders sharing service](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#Samba_Server)

[list][*]Read [#General Notes](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#General_Notes)


[*]Read [#How to add extra repositories](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_add_extra_repositories)[/list]

```
sudo apt-get install samba smbfs
```

Other links to help you out.

[Ubuntu Guide](http://ubuntuguide.org/) [Ubuntu Documents](http://doc.gwos.org/doku.php/doc:ubuntu) [Full Circle Magazine](http://fullcirclemagazine.org/) [Planet Ubuntu](http://planet.ubuntulinux.org/) [Planet Ubuntu Users](http://www.ubuntuweblogs.org/) [Ubuntu News](http://www.ubuntu-news.net/)  [Ubuntu Tips](http://www.ubuntutips.net/) [Ubuntu Geek](http://www.ubuntugeek.com/) [Fresh ubuntu](http://www.freshubuntu.org/) [Ubuntu Live Stats](http://www.ubuntustats.com/) [Ubuntu Video](http://www.ubuntuvideo.com/) [Launchpad.net](https://launchpad.net/) [Debuntu](http://www.debuntu.org/)       [Ubuntux](http://www.ubuntux.org/) [Ubuntu Heaven](http://ubuntuheaven.blogspot.com/) [UbuntuHQ](http://www.ubuntuhq.com/) [Behind Ubuntu](http://behindubuntu.org/) [Medibuntu](http://medibuntu.sos-sts.com/) [Ubuntu Click And Run](http://www.getdeb.net/) [Ubuntu Artwork](http://www.volvoguy.net/ubuntu/) [Ubuntu Blog](http://ubuntu.wordpress.com/) [Debian Admin](http://www.debianadmin.com/)

---

### Post by SGAZ on 2008-04-02
You may need to enable Port Forwarding on your router to allow access on the Samba ports of your various machines' local  IPs.  Samba ports are 137-139.

---

### Post by JayDeePlus on 2008-04-02
is port forwarding going to effect the connection i already have.........because whats funny is that i'm able to get to the internet from the machine with ubuntu......... so that mean it's able to see the network and speak to it........because i'm able to ping other computers on the network........just when i go to Place> Network> And go to the shared computer...........it say unable to display content this folder.....

---

### Post by SGAZ on 2008-04-02
Port forwarding will just open up additional ports on your router for specific machines - ports and machines specified by you.  It will not take anything away from your existing connectivity.

---

### Post by JayDeePlus on 2008-04-02
here's my thing..........i'm not trying to share files on the ubuntu machine.........i'm trying to access the files on the XP machine from the ubuntu machine and recieving an error message "ubable to display folder content" i'm not getting error numbers or any details then that in the little window that popup. I'm able to see XP/other computer from ubuntu machine, but not able to display file contents or see anything on the other computers. but this computer/ubuntu machine is able to get online. i am actually on this ubuntu machine right now............i juss would like to display content off of other computers and i'm farely new to unix OS's..........

what is sambo..........i understand that i'm suppose install it, i have done so. But, i'm not able to find the program in any menu at the top left of a workspace. Is this a feature of another program? or, will it apply settings to The Network place when i try to access other computers on the network?........can someone plzzzzzzzz help me......lord!!!!! lol

---

### Post by JayDeePlus on 2008-04-02
is there a permissions problem here?

---

### Post by Iowan on 2008-04-02
Installing Samba-server  is the first step.  There is a **/etc/samba/smb.conf** file that will likely require some tweaking. [Here]("http://ubuntuforums.org/showthread.php?t=202605") is a good starting point.

---

### Post by evilbuntu on 2008-04-02
sorry forget my post here......

---

### Post by SGAZ on 2008-04-03
> **JayDeePlus said:**
> is there a permissions problem here?

If your XP machine has file sharing turned on and you are sharing files between your XP machines then probably not.

> **JayDeePlus said:**
> what is sambo..........

Samba is a protocol used for file sharing. In this case, between Linux and Windows machines.* (when you try to connect to your XP machines you should see smb://[windows machine name] in the location bar - 'smb' equals Samba.)*  Regardless of whether you have the Samba package installed this is the way Linux machines read and write files on Windows Shares.  If you have installed Samba it runs as a service.  You can start it and stop it in System-Administration-services menu.  

'smb' protocol connections use ports 137-139. Setting your router to allow these ports to be used by the IP addresses of your sharing machines (XP and Ubuntu) for both UDP and TCP connections could solve your problem.  It does not matter which machine is hosting the shared files.  If the router is blocking smb traffic for either machine then the smb connection will not be made.

Getting to the Internet from your Ubuntu machine or seeing other machines on your network does not utilize the same network protocols or ports as 'smb' file sharing.

I was getting the same messages as you until I opened these ports on my router.

---

### Post by JayDeePlus on 2008-04-03
am i suppose to manually add this ports?...........i see the ubuntu machine ip address on the router......do i change the ports of that ip?........or is there a specific ip i'm to add for sambo......

---

### Post by SGAZ on 2008-04-03
In your router admin/set up you should find a section called Port Forwarding (Mine is in a section about gaming and network applications). In that section you should be able to designate port numbers and the ip addresses that are allowed to use them.  I have Linksys Router and mine looks something like:

Application: samba (user defined really)
Start Port : 137
End Port: 139
TYPE:  TCP or UDP or Both (select Both if it is an option)
IP: the local router IP of the machine (192.168.... whatever)

If "both" is not an option in TYPE then you can do a separate line for TCP and UDP.

You should create a separate entry for each machine's IP( XP and Ubuntu).

At the bottom of the router admin  page you made the changes on  there should be a "save" button. Save your changes.

After this you will know for sure that your Router is not blocking your file sharing.

---

### Post by JayDeePlus on 2008-04-03
i have a belkin router......... i don't see anything that say port forwarding........but, there is something that say's virtual settings........and in this tab this is what it say

> Firewall > Virtual servers

 	
  	This function will allow you to route external (Internet) calls for services such as a web server (port 80), FTP server (Port 21), or other applications through your Router to your internal network. More Info

So i'm guessing this is where i would add smb application in at, also it had a list of programs that the router would normally block and a option to allow programs or add a program. so i titled the program SMB for discription, added 2 lines one to TCP and one for UDP........there was not an option in the drop down for both for type........then it says private ip address...........so i guess in this field it's asking for the ip address of the ubuntu machine?...........so i change that to the ubuntu machine......

for the first line it says something about "inbound port" so i'm assuming this is where you wanted me to add port 137 and 139..........now it's 2 boxes..........so i do the left box with 137 and the right box 139?..........or should i do both 137 (because there is other probrams enable, like myspace, that has the same number in both boxes) and the second like i added do both boxes 139?..........

---

### Post by JayDeePlus on 2008-04-03
still need help here..........](*,)]

---

### Post by JayDeePlus on 2008-04-03
ok i got off the phone with belkin tech support........... they walked me through adding those port to the router............not able to access files on XP machine.........then they toke me to set the ip address of ubuntu machine outside of the routers firewall.........did that and still not able to access files on XP machine............then they toke me to turn off the routers firewall completely...........this should enable all ports to the router..........tried to access files off of XP machine from ubuntu machine and still was not able to access................now i went to system > admin > Services .........and folder sharing service (Samba) is enabled...............so what's the deal here?.......

---

### Post by SGAZ on 2008-04-03
Post Removed as it was two minutes too late :)

---

### Post by SGAZ on 2008-04-03
Well, It's not your router or the smb ports.  Which is good to know but disappointing that it was not the fix you needed.

You should probably look into the [**Networking and Wireless forums**]("http://ubuntuforums.org/forumdisplay.php?f=136") and do a search for the Message you get when trying to connect to your XP shared folders.  I'm sure there are plenty of folks who have had the same problem.

Good luck, I'm sure you'll get it going soon.

---

### Post by JayDeePlus on 2008-04-03
> Within Nautilus (your file browser), try clicking the location bar (hit Ctrl+L or click View -> Location Bar if it's hidden), and type:
Code:

smb://IP.ADD.RE.SS

Replace the caps with the IP address of the Windows machine you're trying to access.

Cheers,

Eiríkr
______________


for some reason.............this worked and that was all.............man this made me feel really stupid..........lol............i need to learn more about linux/ubuntu programming i think.........

---

