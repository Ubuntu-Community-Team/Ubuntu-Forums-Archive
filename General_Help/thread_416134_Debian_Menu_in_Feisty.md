---
title: "Debian Menu in Feisty?"
date: 2007-04-20
forum: General Help
---

### Post by Ziggy72 on 2007-04-20
I installed the Debian menu using Automatix but there are no entries in Applications > Debian. I've tried uninstalling and reinstalling and I've also tried:

```

sudo aptitude install menu

```

... but no success.

I've had no trouble with this in either Dapper or Edgy. Any ideas appreciated.

Update:

This matter is now**[COLOR="Red"] Resolved[/COLOR]**. Please see my last post for details of how the problem can be corrected.

---

### Post by jiminycricket on 2007-04-20
I seem to remember that the Debian menu is hidden by default in Alacarte...can you try right clicking on "Applications", choose edit menus, then check the box that says Debian?

---

### Post by Ziggy72 on 2007-04-20
Thanks, but if the Debian box is ticked and there are no Debian entries, the Debian menu won't show in the Applications menu and this is what's happening at present.

---

### Post by ubuntu27 on 2007-04-20
Make sure the extra repos are enabeld (Multiverse& _Universe_)

then do 
```

sudo apt-get update
```


```
sudo apt-get install menu
```


EDIT:

Debian menu is is the Universe repository. If you have problem downloading it.
You can download it using your favorite browser:

[http://packages.ubuntu.com/feisty/admin/menu](http://packages.ubuntu.com/feisty/admin/menu)

---

### Post by Ziggy72 on 2007-04-20
Thanks - Multiverse and Universe are both enabled. The output from
```

sudo apt-get install menu

```
is
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
menu is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
which suggests to me that the system thinks that the Debian menu is installed ok. But nothing shows.....

---

### Post by Ziggy72 on 2007-04-20
Update:

I've just downloaded and reinstalled 

  menu_2.1.32_i386.deb

but still nothing shows in Alcarte. Is this only my problem or are other Feisty users having trouble showing the Debian menu too?

---

### Post by ubuntu27 on 2007-04-20
Back when I was using Breezy, I had similar problem.
Even though I had installed Debian menu with apt.
It didn't show up.

So I was playing around with the Menu Editor (ALcate?) trying to enable Debian. 

I was licking multiple times to the check box next to Debian in the Menu Editor.

ANd suddenly, it worked.

---

### Post by Ziggy72 on 2007-04-20
Ok thanks. I too have had some trouble in the past with the Menu Editor not behaving exactly as I would expect (mainly ticking not working promptly). I think I'll have to accept defeat for now and hope that time may bring some resolution. If the Debian menu doesn't appear in a few days I'll try another round of uninstallation/reinstallation/menu editing:(  Sigh........

---

### Post by flyingbrass on 2007-04-21
Try restarting gnome-panel:

killall gnome-panel

---

### Post by Ziggy72 on 2007-04-21
The problem is now resolved. Thanks to those who made suggestions.

After trawling the web and trying out several options I finally used the following strategy:

1) Used  Synaptic Package Manager to reinstall menu.
2) Used  Synaptic Package Manager to reinstall menu-xdg.

Rebooted and checked the Applications Menu - still no items listed in the Debian menu.

3) Executed the following:

```

sudo dpkg-reconfigure menu
sudo dpkg-reconfigure menu-xdg

```

Checked the Applications menu...... **[B][COLOR="Red"]SUCCESS!!!!!![/COLOR]**[/B] The Debian menu is there in all its glory.

---

### Post by Shinobi326 on 2007-04-25
Thanks for posting your solution in this thread.  I've been having the same exact problem with Feisty too.  I can't wait to go home and resolve this issue.

I'm hoping that Debian will allow me to see all of the stuff I've installed but hasn't shown up in the regular menu.  It boggles the mind that you can actually install stuff and yet not have a menu link to run it.

I hope the capabilities of Debian to show everything will be incorporated into future releases of Ubuntu.

---

### Post by lemming622 on 2007-04-29
I'm sorry but that didn't work for me.  Any clues as to why?

---

### Post by fsando on 2007-05-08
Hi - just what I needed - thanks
I only did the reconfigure part nothing else and now it works

---

### Post by tfejos on 2007-06-03
> **fsando said:**
> Hi - just what I needed - thanks
I only did the reconfigure part nothing else and now it works

Lucky you. I've  run into this problem:
[https://bugs.launchpad.net/ubuntu/+source/menu-xdg/+bug/71317](https://bugs.launchpad.net/ubuntu/+source/menu-xdg/+bug/71317)
[https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/71276](https://bugs.launchpad.net/ubuntu/+source/xubuntu-meta/+bug/71276)

And had to add this menu entry by hand to /etc/xdg/xfce4/desktop/menu.xml

[FONT="Courier New"]<menu name="Debian Menu" icon="debian">
            <include type="file" src="/etc/xdg/xfce4/desktop/menudefs.hook" />
</menu>[/FONT]

---

### Post by fsando on 2007-06-04
Yeah! I got that too on my other laptop (Xubuntu 6.10). I'll use your advice.

---

### Post by RedSquirrel on 2007-06-04
> **lemming622 said:**
> I'm sorry but that didn't work for me.  Any clues as to why?

After you install the menu package:

```
sudo apt-get install menu
```try running:

```
sudo update-menus
```That should generate the Debian menu. I've never had to do any of that "reconfigure" stuff mentioned earlier.

---

### Post by iSam24 on 2007-08-27
i have the same problem but i cant get mine to work i am using dapper drake

---

### Post by R_U_Q_R_U on 2007-08-31
I have followed the suggestions in this thread with no success. In /etc/xdg/menus/application.menu there is this code:

```
 <!-- The Debian menu -->
  <Menu>
    <Name>Debian</Name>
    <MergeFile>debian-menu.menu</MergeFile>
    <Directory>Debian.directory</Directory>
  </Menu>

```There is also a file called debian-menu.menu. It is populated with all the entries that should be there but if fails to appear in the Application menu.

---

