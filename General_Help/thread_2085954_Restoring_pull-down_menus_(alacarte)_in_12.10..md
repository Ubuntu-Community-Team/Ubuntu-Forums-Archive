---
title: "Restoring pull-down menus (alacarte) in 12.10."
date: 2012-11-19
forum: General Help
---

### Post by bilkay on 2012-11-19
After "upgrading" to 12.04, I no longer have pull-down menus (alacarte) that function. I can use alacarte to edit menus, but I can't find how to invoke the menus.

Help?

---

### Post by malspa on 2012-11-19
12.10 is not an LTS version...

---

### Post by dannyboy79 on 2012-11-19
install gnome-session-fallback and login to the gnome classic session. it won't use Unity.

---

### Post by bilkay on 2012-11-19
> **dannyboy79 said:**
> install gnome classic and login to the gnome classic session. it won't use Unity.
How does one go about doing that?

---

### Post by bilkay on 2012-11-19
> **malspa said:**
> 12.10 is not an LTS version...
That's helpful!

---

### Post by dannyboy79 on 2012-11-19
> **bilkay said:**
> How does one go about doing that?

go to your software center and type in gnome-session-fallback. then at the login prompt, choose which session you want to log into.

---

### Post by The Cog on 2012-11-19
A number of people have migrated to Xubuntu, Kubuntu or Lubuntu - you might find those worth a try. I gather that gnome classic will also be dropped from Ubuntu eventually, as the gnome developers have ceased work on gnome2.

---

### Post by Frogs Hair on 2012-11-19
Although I like Unity and the Gnome Shell I find XFCE to a very nice but more traditional desktop . It also looks nice with minimal effort. Unless you install 12.04 Classic Gnome may be gone by 13.04 because Gnome is dropping it with the release of Gnome 3.8. KDE is nice if you like to customize also.

---

### Post by bilkay on 2012-11-19
> **dannyboy79 said:**
> go to your software center and type in gnome classic. then at the login prompt, choose which session you want to log into.
I had tried that but didn't notice the "Show 1 technical item" link at the bottom. Now it sucks a little less. It would suck even less if I could add applets to the panel bars at the top and bottom of the screen. I can't even add a launcher to the desktop. What's up with that? Are they trying to make this a Windoze clone?

---

### Post by bilkay on 2012-11-19
> **Frogs Hair said:**
> Although I like Unity and the Gnome Shell I find XFCE to a very nice but more traditional desktop . It also looks nice with minimal effort. Unless you install 12.04 Classic Gnome may be gone by 13.04 because Gnome is dropping it with the release of Gnome 3.8. KDE is nice if you like to customize also.
Suppose I wanted to switch to kubuntu. Is there a relatively painless way to make the switch?

---

### Post by Bucky Ball on 2012-11-19
As noted, 12.10 is not an LTS release, therefore your thread title is misleading and doesn't describe your issue.

I have changed the title on the first post and this will be effective on the title that appears in the first post, the subscribed threads and the main thread list only. This might improve your chances of getting appropriate help. 

If you would like to edit the title to something else again, feel free to do so by editing the first post and hitting 'Go Advanced' then editing the title. 

BB

---

### Post by dannyboy79 on 2012-11-19
> **bilkay said:**
> Suppose I wanted to switch to kubuntu. Is there a relatively painless way to make the switch?yes, you can. Read about it here: [http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)

Sorry, and to fix my earlier post I meant to install gnome-session-fallback.

---

### Post by MutantJohn on 2012-11-19
How can 12.10 possibly suck? It's got Gnome 3.6 and once you get used to it, Gnome 3 is awesome. Unity's OpenGL benchmarks are way down here and Gnome's are way up there. I can finally alt-tab out of Heroes of Newerth!

Though I will say one thing, between nautilus, the gnome-shell and Xorg, my CPU is idling at around 40% usage which is pretty interesting to say the last. CPU frequencies are all at their lowest, temps are normal too, so I don't know if this is the result of proper kernel optimization or heavy and clunky code. I say optimization in the sense that yes, empty threads are lame so why not do something pretty in the meantime and actually put this CPU to use.

---

### Post by vasa1 on 2012-11-20
> **Bucky Ball said:**
> As noted, 12.10 is not an LTS release, therefore your thread title is misleading and doesn't describe your issue.
....
Based on the actual contents of the post, the title is totally inappropriate, not just misleading.

> After "upgrading" to 12.10, I no longer have pull-down menus (alacarte) that function. I can use alacarte to edit menus, but I can't find how to invoke the menus.

Help? 

Of course, the thread has digressed even further. I don't see even a single response relating to the original issue.

---

### Post by bogan on 2012-11-20
Hi!, **bilkay,**

If what you want is the traditional drop-down menus, together with Ubuntu 3D, and/or Gnome Classic, then install 'ClassicMenu Indicator':```
sudo apt-add-repository ppa:diesch/testing
sudo apt-get update
sudo apt-get install classicmenu-indicator
```I[I]t is listed as for 12.04, but runs OK in 12.10.

[/I]Chao!, **bogan**.

---

### Post by bilkay on 2012-11-20
> **Frogs Hair said:**
> Although I like Unity and the Gnome Shell I find XFCE to a very nice but more traditional desktop . It also looks nice with minimal effort. Unless you install 12.04 Classic Gnome may be gone by 13.04 because Gnome is dropping it with the release of Gnome 3.8. KDE is nice if you like to customize also.
Where does "Unity" come from? It's not on my list of available sessions.

---

### Post by zombifier25 on 2012-11-20
> **bilkay said:**
> Where does "Unity" come from? It's not on my list of available sessions.

Unity is the session listed as Ubuntu, which is probably the one you're using right now.

Your original post asked for how to get the classic menu in Unity. Bogan's post has answered just that.

---

### Post by bilkay on 2012-11-20
> **zombifier25 said:**
> Unity is the session listed as Ubuntu, which is probably the one you're using right now.

Your original post asked for how to get the classic menu in Unity. Bogan's post has answered just that.
Actually, it didn't answer the question of how to get the menu in Unity. I'd settle for being able to create a launcher for programs I create, but I can't find any way to do that other than typing the program name in a terminal. I find that very unsatisfactory. If I wanted that kind of inflexibility, I'd stick with Windoze.

---

### Post by bogan on 2012-11-20
Hi!,** bilkay**,

You Posted> :Actually, it didn't answer the question of how to get the menu in Unity.I had Posted:> If what you want is the traditional drop-down menus, together with Ubuntu 3D, _**Ubuntu 3D is UNITY,**_ and ClassicMenu Indicatorworks with Unity.

Try it and see, and if you want to create launchers for your self-made programs, study the forums that tell you how to do so, just use Search..

Chao!, **bogan**.

---

### Post by bilkay on 2012-11-20
> **bogan said:**
> Hi!,** bilkay**,

You PostedI had Posted:_**Ubuntu 3D is UNITY,**_ and ClassicMenu Indicatorworks with Unity.

Try it and see, and if you want to create launchers for your self-made programs, study the forums that tell you how to do so, just use Search..

Chao!, **bogan**.
The only sessions (other than gnome) I have on the login screen are ubuntu and ubuntu 2D. What is ubuntu 3D?

---

### Post by bilkay on 2012-11-20
> **bogan said:**
> Hi!,** bilkay**,

You PostedI had Posted:_**Ubuntu 3D is UNITY,**_ and ClassicMenu Indicatorworks with Unity.

Try it and see, and if you want to create launchers for your self-made programs, study the forums that tell you how to do so, just use Search..

Chao!, **bogan**.
Thanks for the suggestion. I was able to create a launcher on my desktop by adding a template in ~/Templates.

```
[Desktop Entry]
Version=1.0
Type=Application
Terminal=false
Icon[en_US]=
Exec=
Name[en_US]=Application launcher
Comment[en_US]=
Name=
Comment=
Icon=
``` I still haven't figured out how to get the ClassicMenu to work with ubuntu (Unity?). That would be nice but not critical. One odd thing was that I was able to drag the desktop launcher onto the launcher bar, but it didn't display the icon - just an empty space, but it did launch the app.

---

### Post by bogan on 2012-11-21
Hi!, **bilkay**,

If you added the ppa, updated and installed the 'ClassicMenu Indicator', its Icon will appear in the Dash display - enter 'Classic' in the search box, and click on the icon.

The first time you do so, and it runs, a Ubuntu logo Icon will appear in the top right toolbar.

From then on, just select that Icon and the usual drop-down menus will appear.

Note that there is no 'Places' menu, and the 'Administration' & 'Preferences' menus are sub-menus of 'System Tools' in the Main menu.

Chao!, **bogan.**

---

### Post by kurt18947 on 2012-11-21
> **bilkay said:**
> Actually, it didn't answer the question of how to get the menu in Unity. I'd settle for being able to create a launcher for programs I create, but I can't find any way to do that other than typing the program name in a terminal. I find that very unsatisfactory. If I wanted that kind of inflexibility, I'd stick with Windoze.

You might be happier with an *buntu version other than Unity such as Xubuntu or Lubuntu. Another thing I've done is to add alternative desktops to Ubuntu.  If you look in the software center, you can download and install Xfce-desktop or LXDE desktop.  You can then log out and when the greeter appears, there's a little gear icon to the right of user names.  Click on that gear and different installed desktops/environments will be listed.  I personally prefer gnome (shell) with some extensions to get a hybrid between the 'traditional' desktop with menus and search apps.  For instance, there are a couple extensions that give application menus when clicked.

If you insist on desktop launchers, you can try this.  It works in gnome:

```
gnome-desktop-item-edit ~/Desktop/ --create-new
```You have to know the command to launch your app, of course and you choose the icon for the launcher.  I use this for administering printers.  The new printers app is a step in the wrong direction but the older one is still available in the repositories and still works.  The same is true of users & groups.

---

### Post by bilkay on 2012-11-21
> **bogan said:**
> Hi!, **bilkay**,

If you added the ppa, updated and installed the 'ClassicMenu Indicator', its Icon will appear in the Dash display - enter 'Classic' in the search box, and click on the icon.

The first time you do so, and it runs, a Ubuntu logo Icon will appear in the top right toolbar.

From then on, just select that Icon and the usual drop-down menus will appear.

Note that there is no 'Places' menu, and the 'Administration' & 'Preferences' menus are sub-menus of 'System Tools' in the Main menu.

Chao!, **bogan.**
Success! It's sucking less and less every day! (By "sucking," I mean being like Windoze.)

Thanks!

---

### Post by Bucky Ball on 2012-11-22
Good news. When/if it's acceptably less sucky please mark the thread as 'Solved' to help others if you willl. ;)

---

