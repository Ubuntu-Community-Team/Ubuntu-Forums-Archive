---
title: "updates, software centre, synaptics not working, Internet, Mozilla  graphi"
date: 2018-06-04
forum: General Help
---

### Post by kelliewilliams on 2018-06-04
[ATTACH=CONFIG]279960[/ATTACH][ATTACH=CONFIG]279961[/ATTACH][ATTACH=CONFIG]279965[/ATTACH][ATTACH=CONFIG]279964[/ATTACH]

Hi, I am having several problems with my Lubuntu 18.04 
1.Which I already put in the forum and seemed to have solved has started again, I am not able to update, the updater notifies me of updates which I click but then the page just disappears and no updates have occurred.I solve the problem by using the terminal and putting the following commands:
sudo apt-get updates
sudo apt-get upgrade
Sudo apt-get dist-upgrade
I then check for updates and my computer is up to date, am I going to have to update through the terminal all the time?
2.Nowhere in the menus can I find the software centre to install any programs etc.
3.When I click Synaptic package manager it circles for me to wait and then  nothing, I have done a SS of the properties if that helps, but it seems  I am unable to use it.
4.The internet cuts off for no reason and I am unable to reconnect unless I reboot my computer. Also I don't seem to be able to have 2 internet providers so as to switch between when I do have problems.
5.A game I try to load in Mozilla (that worked in Mozilla on my windows os) gives me a flickering screen between the 2 images I have attached above, the same game works fine, albeit slow on the Chromium browser.
Hoping someone can assist me (I can be extremely dumb so bear with me. :) )
Thanks in advance.

---

### Post by Dennis N on 2018-06-04
> Nowhere in the menus can I find the software centre to install any programs etc.
You should have an application called 'Software' found under 'System Tools'. At least it has categories you can browse through, with some minimal descriptions of the Applications. It should be part of your default Lubuntu 18.04 installation (if you did a new install). If not, package name to install it is 'gnome-software'. It can apparently also handle updates to your system. I say 'apparently' because I have been relying on the regular software updater for that, and not tried 'Software' for updating purposes.

---

### Post by kelliewilliams on 2018-06-04
Software isn't there not anywhere looked on all of the system tools, accessories and preferences.... nothing, except the software updates and synaptics package manager, neither of which work- :(

---

### Post by deadflowr on 2018-06-04
Typically when the update graphical interface(such as software updater or synaptic) is gong bonkers it means something is wrong with the update functions.
post the output for the apt-get update commands.
TYhe proper command is
```
sudo apt-get update
```
I do not know if *sudo apt-get  updates* in your original post was intentional or not.
But that would be wrong.

---

### Post by kelliewilliams on 2018-06-04
[IMG]https://scontent.flis3-1.fna.fbcdn.net/v/t1.15752-9/34463149_2105070986441929_1381709516202049536_n.jpg?_nc_cat=0&_nc_eui2=AeGIpb83q-fZOke5zo8qUULR6GMRV3GeZI7dKjvl_dXytTujbmJp4qE2_MF8oQYEmlRniwz-BoBx1Oa1Lf75eUCzsZ2_9LYadbhgFFud0__LZA&oh=1ddde520d0c2f38748e0c27e56012265&oe=5B7B4063[/IMG]

---

### Post by Dennis N on 2018-06-04
To install (or see if it's already installed) run in terminal:

```
sudo apt-get install gnome-software
```

if already on your system, you would see this:

```
dmn@Sydney:~$ sudo apt-get install gnome-software
[sudo] password for dmn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gnome-software is already the newest version (3.28.1-0ubuntu4).

```
--------------------------------------
Comment on screenshot tool in Lubuntu: I suggest installing gnome-screenshot. Works better than Lubuntu's scrot, and will capture menus while scrot does not (gnome-screenshot image below shows where I have 'Software'). No new dependencies were installed with gnome-screenshot on my system, so that is good too.

---

### Post by monkeybrain20122 on 2018-06-04
Lubuntu is preinstalled with synaptic package manager as your screenshot shows. It is much better than gnome-software anyway. gnome-software has only a small fraction of software you can find in synaptic, it is bloated piece of junk

---

### Post by kelliewilliams on 2018-06-04
Hi, Sorry, in the original post I did put updates but in the terminal it was update. ;) It does update when I do that in the terminal but I thought that it would also solve the problem of having to go through the terminal. Not that it is a big issue, I will just wait until I have a few updates to do. :)

---

### Post by kelliewilliams on 2018-06-04
So I did what you said and have managed to install gnome software on my computer, I tried the same for synaptic package manager but only got this far, so maybe no giving the correct code.     [ATTACH=CONFIG]279967[/ATTACH]

Many thanks :)

---

### Post by kelliewilliams on 2018-06-04
Although it appears in the menu table synaptic package manager it doesn't open when clicked, so I am assuming there is a fault somewhere. :)

---

### Post by Dennis N on 2018-06-04
> **kelliewilliams said:**
> Although it appears in the menu table synaptic package manager it doesn't open when clicked, so I am assuming there is a fault somewhere. :)
One thing to check is to see if the command to start it is correct. Please post the result of this command in the terminal:
```
cat /usr/share/applications/synaptic.desktop | grep Exec
```

---

### Post by kelliewilliams on 2018-06-05
[ATTACH=CONFIG]279970[/ATTACH] Results. :(

---

### Post by Dennis N on 2018-06-05
The command is correct, so that's not the problem. I would try the command itself in a terminal to see if there are error messages; these might point to the problem. Do not use sudo in this command. Normal behavior is shown in my screenshot below - the authentication dialog pops up (as shown). Do you get the dialog, or not?

---

### Post by Dennis N on 2018-06-05
> **kelliewilliams said:**
> So I did what you said and have managed to install gnome software on my computer, I tried the same for synaptic package manager but only got this far, so maybe no giving the correct code.Many thanks :)

Problem here is that you don't have the correct package name (or file name it is kept under), which is just 'synaptic' (although the program is named 'Synaptic Package Manager') confusing? 
```
sudo apt-get install synaptic
```
would work. This would probably inform you it is already installed and the latest version.

Also, since gnome-software was apparently not installed, this means something different about yours and the installation from the Lubuntu 18.04 install media, where the manifest (list of included packages) shows gnome-software is installed with it. Reference link to manifest:

[http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/lubuntu-18.04-desktop-amd64.manifest](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/lubuntu-18.04-desktop-amd64.manifest)

Did you upgrade from another Lubuntu release? Did you add Lubuntu-desktop to standard Ubuntu? If so, that may be a factor.
If you have time, you might just reinstall and probably fix the problem, but be sure to use the latest Lubuntu 18.04 install media if you didn't previously. 

[http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/](http://cdimage.ubuntu.com/lubuntu/releases/18.04/release/)

---

### Post by kelliewilliams on 2018-06-05
So for this code it gave me this..  [ATTACH=CONFIG]279981[/ATTACH]

---

### Post by kelliewilliams on 2018-06-05
On trying this I got [ATTACH=CONFIG]279982[/ATTACH] Now I tried this one 3 times just because I thought I may have inadvertently miss typed my password but I hadn't. So maybe the answer is as you say to do a reinstall. Incidently is there anywhere I can go to get a list of commands for the terminal, or at least the most commonly used ones?

---

### Post by Dennis N on 2018-06-05
Well, this is useful in that it narrows the problem to the authentication. With Google search on the error message you posted, I found this discussion:
[https://askubuntu.com/questions/885831/synaptic-does-not-work](https://askubuntu.com/questions/885831/synaptic-does-not-work)
but it is about Ubuntu MATE. Nevertheless, the suggestion there might apply here too. So, you can check if Lubuntu's "PolicyKit Authentication Agent" is running. For Lubuntu, its **lxpolkit**. If running, you should see it in **System Tools > Task Manager**. See attached image!

---

### Post by kelliewilliams on 2018-06-06
I don't have lxpolkit so it seems something is really amiss, so maybe better I download Lubuntu 18.04 and install from usb (my cd/dvd player doesn't always work) Last timer I think I downloaded 16.04 and then upgraded to 18.04. Thanks for all your help :)

---

### Post by Dennis N on 2018-06-06
> **kelliewilliams said:**
> I don't have lxpolkit so it seems something is really amiss, so maybe better I download Lubuntu 18.04 and install from usb (my cd/dvd player doesn't always work) Last timer I think I downloaded 16.04 and then upgraded to 18.04. Thanks for all your help :)

Before you do any reinstall, just install lxpolkit and you may well solve the problem.

```
sudo apt-get install lxpolkit
```

After install, restart the computer.

---

### Post by kelliewilliams on 2018-06-06
Aha! OK installed lxpolkit, went back to the  synaptic-pkexec and  although it seemed something had not gone quite right I then tried to  open Synaptic package manager and  hey presto it opened. :)   [ATTACH=CONFIG]280001[/ATTACH][ATTACH=CONFIG]280002[/ATTACH][ATTACH=CONFIG]280003[/ATTACH]
So one last tiny question is there a command I can use to check the whole system is installed and running correctly?

Irrespective of my last question I would just like to take this opportunity to thank you for your patience and help is very very much appreciated. :KS

---

### Post by #&amp;thj^% on 2018-06-06
Agreed Dennis N is a very nice addition to our highly valued members here in UF.
And if I may be bold enough to add:
```
sudo apt autoremove
```
Will help prevent future problems with the package manager. :)
Kind Regards

---

### Post by Dennis N on 2018-06-06
> **kelliewilliams said:**
> Aha! OK installed lxpolkit, went back to the  synaptic-pkexec and  although it seemed something had not gone quite right I then tried to  open Synaptic package manager and  hey presto it opened. :)  So one last tiny question is there a command I can use to check the whole system is installed and running correctly?

Irrespective of my last question I would just like to take this opportunity to thank you for your patience and help is very very much appreciated. :KS

Glad it worked. Sometimes it's more satisfying to know you fixed something than go for the new install. lxpolkit was used in Lubuntu 16.04, so somehow it got lost. lxpolkit is pretty important for the system to be working right. Not aware of any system checkup thing you can use - sorry. 

 In the future, Synaptic should start as expected from the Main Menu.

Suggest you install **gnome-screenshot** for screenshots. Maybe you already did that?
Suggest you install **gnome-system-monitor** as a supplement to task manager. It provides more information and also shows download speeds.

---

### Post by kelliewilliams on 2018-06-06
Hi, I did the autoremove and it did bring with it 2 warnings, they mean nothing to me but I'm sure they will to you. If I need do anything about them you will need to explain how i do it. :) Thanks.

---

### Post by #&amp;thj^% on 2018-06-06
It will help us/me more to show us the warnings that you saw in the terminal, otherwise we are just stabbing in the dark. :)
To copy text from the terminal, highlite the text with your mouse and either right click copy or use the keyboard and use (ctrl + shift + c ) then paste to a text editor like gedit or Leafpad. 
And then paste them bach here with code tags to preserve the format this makes it easier to read. 
Thanks

---

### Post by kelliewilliams on 2018-06-06
:) I cannot take the credit for fixing the problems, without your help I would have been tearing my hair out. I did already download gnome-screenshot and have now also downloaded gnome-system-monitor. The lxpolkit you got me to fix worked a treat, because even though I had the software centre I wasn't able to install any of the programs, so decided on a fresh install and got unetbootin through the terminal, but again I clicked and nothing happened but as soon as Lxpolkit was fixed it worked as do the software centre and the synaptic package manager. :) so from my original post I have 1, 2, and 3 all sorted and working well, I am going to see if I have any additional drivers for my graphics and maybe that will solve problem nº5 and then there will just be nº 4 to sort which isn't a big deal just irritating. Oh and can I uninstall things like the Bluetooth adapter and manager and Xvt?

---

### Post by kelliewilliams on 2018-06-07
[ATTACH=CONFIG]280016[/ATTACH][ATTACH=CONFIG]280017[/ATTACH]I could have sworn I attached these yesterday. I have since done another auto remove and all seems ok [ATTACH=CONFIG]280018[/ATTACH]So again thanks muchly :):KS

---

### Post by kelliewilliams on 2018-06-08
Resolved the Internet issue so no help needed on that now. Thanks all who helped.:)

---

