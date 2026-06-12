---
title: "[SOLVED] Spherical Cube ?"
date: 2008-06-26
forum: General Help
---

### Post by misterhead on 2008-06-26
I just stumbled across this 
[http://www.gnome-look.org/content/show.php/EarthDesktop?content=84070](http://www.gnome-look.org/content/show.php/EarthDesktop?content=84070)
and can't, for the life of me, figure out how to get compiz to do what this is supposed to do.

---

### Post by DaymItzJack on 2008-06-26
> **misterhead said:**
> I just stumbled across this 
[http://www.gnome-look.org/content/show.php/EarthDesktop?content=84070](http://www.gnome-look.org/content/show.php/EarthDesktop?content=84070)
and can't, for the life of me, figure out how to get compiz to do what this is supposed to do.

It's part of the new compiz, you have to compile it from source if you want it.

---

### Post by misterhead on 2008-06-26
Ah... Well I guess it's about time I learn how to do that, then, huh? I have like 5 hours of experience with C++. Is there some sort of app or utility that I would need similar to Visual C++ or whatever to do this sort of thing in Linux?

---

### Post by 16777216 on 2008-06-26
Use these repos

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main
deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

---

### Post by rainwalker on 2008-06-27
Just be warned, the latest versions of Compiz that you will get from those repos may not be very stable (or at least as stable as the version in the repos)

---

### Post by misterhead on 2008-06-27
No Worries. That Sh*t's WAY over my head. I don't know where to begin with those links above.

---

### Post by 16777216 on 2008-06-27
To use the repository addresses above just follow these simple steps.

1: On your menu go to **System > Administration > Synaptic Package Manager**

2: Enter your login password

3: In Synaptic's **Settings** menu, choose **Repositories**. The Software Sources window will appear.

4: Click the **Third-Party Software** tab

5: Click the **Add...** button near the bottom of the window. A new window will appear.

6: Copy/paste the first line I gave you in the previous post then click the **Add Source** button.

7: Repeat steps 5 & 6 but add the second line.

8: Close the Software Sources window.

9: Click the **Reload** button near the top of the Synaptic window.

10: When that has finished click the **Mark All Upgrades** button ( it may give you a warning ) click the **Mark** button.

11: Then click the **Apply** button near the top of Synaptic and then the **Apply** button on the Summary window.

12: Log out then back in to reload Compiz.

And as rainwalker pointed out these may not be the most stable, but I have not had any problems out of the packages,... yet.

---

### Post by Genius314 on 2008-06-27
How recent/how updated is that repository? Right now I just use a script to update Compiz from Git, but would the repositories be better?

---

### Post by DXM31 on 2008-06-27
> **16777216 said:**
> To use the repository addresses above just follow these simple steps.

1: On your menu go to **System > Administration > Synaptic Package Manager**

2: Enter your login password

3: In Synaptic's **Settings** menu, choose **Repositories**. The Software Sources window will appear.

4: Click the **Third-Party Software** tab

5: Click the **Add...** button near the bottom of the window. A new window will appear.

6: Copy/paste the first line I gave you in the previous post then click the **Add Source** button.

7: Repeat steps 5 & 6 but add the second line.

8: Close the Software Sources window.

9: Click the **Reload** button near the top of the Synaptic window.

10: When that has finished click the **Mark All Upgrades** button ( it may give you a warning ) click the **Mark** button.

11: Then click the **Apply** button near the top of Synaptic and then the **Apply** button on the Summary window.

12: Log out then back in to reload Compiz.

And as rainwalker pointed out these may not be the most stable, but I have not had any problems out of the packages,... yet.

I did all that and now nothing works.:confused:
I can't even get to advance desktop settings, my theme is gone...
What happend?

---

### Post by 16777216 on 2008-06-27
1: I don't know how up to date it is.
2: I am sorry to hear that this broke your setup it worked flawlessly for me. What kind of errors are you getting perhaps we can find a solution.

I forgot to mention [http://forum.compiz-fusion.org/](http://forum.compiz-fusion.org/) is a great place to find help with Compiz Fusion

---

### Post by DXM31 on 2008-06-27
Well Kiba-dock still works which is even more confusing because I didn't think that would work without compiz

---

### Post by DXM31 on 2008-06-27
> **16777216 said:**
> 1: I don't know how up to date it is.
2: I am sorry to hear that this broke your setup it worked flawlessly for me. What kind of errors are you getting perhaps we can find a solution.

I don't get any error, when I clicked on ccsm nothing happens and when I change to change the theme in emerald nothing happens
So I uninstalled CCSM and reinstalled it and it doesn't work.
Looks like I am going to the "how do I remove and reinstall Compiz" threads
Prolly the main problem is I am running 7.10

---

### Post by 16777216 on 2008-06-27
> Prolly the main problem is I am running 7.10Yeah, the repo is for hardy.

open synaptic and click the Origin button under the catigory list pick the repo, and remove everything compiz, remove the repo, then search for compiz and reinstall it.

---

### Post by DXM31 on 2008-06-28
I decided to go ahead an upgrade to Hardy.
But it didn't fix anything.
I still have no compiz(but ccsm works?), no windows boarders, I can't grab a window and drag it, no opacity...but Kiba-Dock works

---

### Post by DXM31 on 2008-06-28
UPDATE
I updated compiz with the repos listed on page one for the spherical cube and everything works better but I can't get emerald themes to work.
It is not a problem...it's an adventure

---

### Post by ans5685 on 2008-06-28
Follow this link:-

[http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

If you do exactly as it says then you should have all the Compiz you need :)

---

### Post by DXM31 on 2008-06-28
> **ans5685 said:**
> Follow this link:-

[http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

If you do exactly as it says then you should have all the Compiz you need :)

Thanks I will take a look at it.
Another thing I noticed is certain things on ccsm won't stay clicked like 3d cube, snow, autumn,...?

---

### Post by misterhead on 2008-06-28
@ 16777216
Now my question is, do you suppose the spherical cube is worth upgrading to Hardy, as I am running Gutsy to? This is a Dell Laptop dual booting XP Pro and Gutsy. I tried Hardy beta when it first came out and had overheating problems immediately. (especially with compiz)I guess all I can do is try it and see.

---

### Post by DXM31 on 2008-06-28
If you are asking me I would say no.
Apparently it takes a better graphics card than I have because it slows everything down when I activate the sphere, so I turned it off.
But now there are other issues like things that worked before no longer work. i.e. 3d cube, snow, autumn,...
I too am running this on a laptop.

---

### Post by misterhead on 2008-06-28
hmmm. Well I just started the download for the Hardy Live cd, but maybee I'll burn it and install it on my desktop with a Radeon 9800 pro, and leave my laptop the way it is. At least the desktop has nothing on it but Hardy at the moment.

---

### Post by xpod on 2008-06-28
> I updated compiz with the repos listed on page one for the spherical cube and everything works better but I can't get emerald themes to work.
**It is not a problem...it's an adventure**

Love the quote,good sig material even:)

---

### Post by 16777216 on 2008-06-28
I started this and now don't know how to finish it.:lolflag:

To fix emerald:
You might want to try putting ```
emerald --replace
```in the **Command** section of the **Window Decoration** plugin

As far as your options not sticking move your **~/.compiz** folder to your desktop and restart compiz, you may have to set all of your plugins up again. If that does not work just move it back.

Another handy thing is fusion icon. ```
sudo apt-get install fusion-icon
```(If you are on hardy) It lets you have a quick and handy on/off/restart, open CCSM/Emerald theme picker, compiz option, all-in-one thingy.

And if hardy over heats your laptop,.. ***Don't use it!*** You don't want to blow your laptop.:(

---

### Post by DXM31 on 2008-06-28
I got Emerald to work, after looking at the FAQ I noticed Emerald was no longer in my startup.
So added it and restarted and bam got emerald.
I will have to try the move compiz and install fusion-icon.
So far Hardy is running just fine. It is just the compiz problem now.
One more thing, all my windows have grey lines around them kind of like glow in some themes but it isn't glowing it is just there and I don't know how to get rid of it.
No matter which theme I choose it is always there?

---

### Post by DXM31 on 2008-06-28
UPDATE
I got 3d to work it is in ccsm>preferences>plug in list
It was disabled for some reason.
Now any ideas about the lines like shooting stars on all my windows.
I know it is some kind of effect but where to shut it off.

---

### Post by borlosky on 2008-06-28
> **16777216 said:**
> To use the repository addresses above just follow these simple steps.

1: On your menu go to **System > Administration > Synaptic Package Manager**

2: Enter your login password

3: In Synaptic's **Settings** menu, choose **Repositories**. The Software Sources window will appear.

4: Click the **Third-Party Software** tab

5: Click the **Add...** button near the bottom of the window. A new window will appear.

6: Copy/paste the first line I gave you in the previous post then click the **Add Source** button.

7: Repeat steps 5 & 6 but add the second line.

8: Close the Software Sources window.

9: Click the **Reload** button near the top of the Synaptic window.

10: When that has finished click the **Mark All Upgrades** button ( it may give you a warning ) click the **Mark** button.

11: Then click the **Apply** button near the top of Synaptic and then the **Apply** button on the Summary window.

12: Log out then back in to reload Compiz.

And as rainwalker pointed out these may not be the most stable, but I have not had any problems out of the packages,... yet.

Works PERFECTLY!!!! Thank you SOOOOOOOO much!!!

---

### Post by 16777216 on 2008-06-28
Well, I am glad it was flawless for somebody. :wink:

---

### Post by KazukiFlame on 2008-06-30
i'm using ubuntu hardy 8.04 gnome

i just updated my compiz from 0.7.4 to 0.7.6, the updated worked perfectly, i'm glad the cylinder and sphere worked. then i realize the cube reflection and some other options r gone. moreover, my compiz snow, atlantis, snowglobe, n everything that was extra stopped working all together.

my guess is i might have to reinstall those, but i lost the link to the addons for gnome, most of the ones i found r for kubuntu n gutsy, not hardy.

---

### Post by DXM31 on 2008-06-30
If you get that working let us know.
I was able to get 3d back, but the other effects snow,... won't work even after I tried to reinstall the effects individually. 
I can see them and they are still set up the way I had them but I can't check them:confused:

---

### Post by misterhead on 2008-06-30
O.K. I bit the bullet and replaced Gutsy with Hardy on my laptop, installed he new compiz, and got the sphere working and everything, but how do I set the 4 sides of the cube to the different wallpapers that are in my original thread-starter. I got the caps, but I can't find the place in this new compiz for the 4 wallpapers.

---

### Post by borlosky on 2008-07-01
Would anyone know how to get the extra plugins to work now? (snow, atlantis, screen saver, snow globe, stack switcher, ect....) i was able to get the plugins installed, but it won't let me check them :(

---

### Post by Eion on 2008-07-01
You can use Fyda's tutorial.  It's pretty easy to follow.  And having easy access to all the new compiz plugins is great :D

[http://forum.compiz-fusion.org/showthread.php?t=1985](http://forum.compiz-fusion.org/showthread.php?t=1985)

---

### Post by 16777216 on 2008-07-01
[LEFT]That is for Compiz 6.0 not Compiz Fusion 7.6

The method will almost certainly fail to make the plugins work. And will most likely cause a complete break in Compiz for those that used the method I posted. I am trying to find a simple fix.[/LEFT]

---

### Post by 16777216 on 2008-07-01
I think most of the "plugin turning it's self off problem" is because gconf has values that some of the plugins don't like.
I have been trying to find a reset all compiz plugin settings method which I believe may solve most of the complaints.
However, I also believe some of this is because some people had extra plugins from a previous install that cant handle the API changes that compiz has had lately.

As a last resort I have found a [thread]("http://ubuntuforums.org/showthread.php?t=781218") that has a method to install Compiz Fusion from git.
Any one who uses this please send all questions to that thread.
As for every one else, I will still try to find a method to reinstall the plugins so that they work.

---

### Post by misterhead on 2008-07-03
Just to update. Mine works now, thanks to everyone here. Hope this thread has helped some others as well. It looks like it so far.

---

### Post by KazukiFlame on 2008-07-05
but what did u do to get it to work again? mine still keeps switching off

---

### Post by larryfroot on 2008-07-06
Hello...
re 4 different wallpapers on the cube...

Yes, there is a very simple way that involves KO'ing gnome providing the wallpaper (via nautilus, bizarrely. Nautilus is also responsible for rendering the desktop icons. Strange world we live in) and giving that job to compiz. Easy as that.

So doing this may be easy but it will take out your desktop icons. However good old cairo (a widget rendering system designed to work with compiz) can be of some help in providing instead a mac-like dock-bar (cairo-dock) which offsets somewhat the loss of functionality. However it does also offer a solid chunk of highly configurable, high quality eye candy which sweetens the blow a bit as well. 

The debs for cairo-dock are here. [http://developer.berlios.de/project/showfiles.php?group_id=8724]("http://developer.berlios.de/project/showfiles.php?group_id=8724")

I used to find cairo-dock unreliable and flakey, but the last two versions have run really well. Some of the features are ace. Just right click on the dock, choose cair-dock/configure. A window pops up, but to get the best out of the config window click the advanced button near the bottom. Personally I rate it more than...

...Avant Window Navigator, which I think is in the repo's. If you find cairo-dock not to your taste or its flakey for you then AWN is your friend. It doesn't seem so configurable as cairo-dock, but some people find it more reliable than cairo-dock and it does do exactly what it says on the box...

Anyways...the first thing to do is to knock out the background rendering in Gnome.

Time to open up gnome configuration editor. The terminal command is sudo gconf-editor ... needless to say this is a powerful tool, so use with respect. You can also go into system/preferences/main menu and clicking on the system tools tab in the left hand panel brought up the option of the configuration editor in the right hand panel. Tick the box and it will be added to your Applications menu under system tools.

OK, config editor is up. Click on little arrow next to apps. Go to nautilus - preferences and uncheck 'show desktop'. Then head towards system/preferences/advanced desktop settings. Head for the desktop cube icon and click it. Then scroll down and under appearance, add the four wallpapers you wish to show one by one. You can add, subtract, change the order of them...check out and voila!

One more handy thing at this stage is to install screenlets (recently updated and looking better all the time), a collection of desktop widgets. The ones from gnome-look are better (and as stable for me) as the screenlets from the repo's. Add the ones you want to your desktop, and in the advanced desktop settings enable the 'widget layer' icon. Now you can toggle the screenlets on and off the desktop by pressing F9. Most cool, and another way to restore extra functionality to your desktop seeing as nautilus will not be drawing icons on it whilst compiz is at the controls. latest debs from...

[http://www.gnome-look.org/content/show.php/Screenlets+0.0.12+final+rev+174?content=73346]("http://www.gnome-look.org/content/show.php/Screenlets+0.0.12+final+rev+174?content=73346")

Finally, things will get downloaded and stored onto the desktop, but you have to navigate to them via nautilus.

Another finally - I like to have a consistent feel across my desktops, so I pop over to the amazing site and resource Deviant Art to download different wallpapers / images by the same artist to give that nice balance of contrast and continuity of style. Cos its nice that way. but each to their own.

---

### Post by Umar07 on 2008-07-06
iv downloaded the new cube and it still doesn't work

---

### Post by DJ_Peng on 2008-07-07
I added the updated code and have the sphere (thanks!) but I'm noticing that my sphere isn't squashed as I saw in the YouTube vid. It's also centered toward the top of my screen rather than in the middle. Anyone have any idea as how to resolve these issues?

---

### Post by sayakb on 2008-07-07
> **DJ_Peng said:**
> I added the updated code and have the sphere (thanks!) but I'm noticing that my sphere isn't squashed as I saw in the YouTube vid. It's also centered toward the top of my screen rather than in the middle. Anyone have any idea as how to resolve these issues?

In CCSM->Cube Deformations and reflections->Deformation tab
Try changing the aspect ratio.
Also, do you have the 3D Windows plugins enabled. Maybe that is pushing the sphere upwards..

---

### Post by larryfroot on 2008-07-07
oooh! I had updated apt with the compiz repos on launchpad, only to find that switching on the sphere with the cube and cube rotation enabled was like nailing jelly to the ceiling. So I used fusion-icon (available thru apt) to switch to loose bindings. Viola. Success.

---

### Post by I[AM]SMRT on 2008-07-08
> **larryfroot said:**
> oooh! I had updated apt with the compiz repos on launchpad, only to find that switching on the sphere with the cube and cube rotation enabled was like nailing jelly to the ceiling. So I used fusion-icon (available thru apt) to switch to loose bindings. Viola. Success.
Yea, toggling on and off loose bindings fixed it for me, too. :D

I'm enjoying my cylinder.

---

### Post by borlosky on 2008-07-08
I was finally able to get all plugins working fine. Here's how I did it:

1: went to add/remove from Applications menu, removed all compiz related software

2: went to Synaptic package manager and COMPLETELY Removed ALL compiz related software

3: Followed steps located here: [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

4: Logged out, then back in. all working fine now!!:KS (all my previous keybindings were saved however, so very little configuration was needed other than just checking the new options)

---

### Post by DJ_Peng on 2008-07-08
> **LinuxIsInnovation said:**
> In CCSM->Cube Deformations and reflections->Deformation tab
Try changing the aspect ratio.
Also, do you have the 3D Windows plugins enabled. Maybe that is pushing the sphere upwards..
It turns out the Reflection was pushing it up. But I tried changing the aspect ratio and it didn't do anything. Now I simply have a huge sphere that takes up my entire desktop and then some (unless I don't deform the caps).

---

### Post by eryksun on 2008-07-08
> **larryfroot said:**
> Yes, there is a very simple way that involves KO'ing gnome providing the wallpaper (via nautilus, bizarrely. Nautilus is also responsible for rendering the desktop icons. Strange world we live in)

GNOME seems to have borrowed a bit from Windows Explorer, which isn't necessarily bad. The desktop is a specialized folder. 

Background images really should be handled by GNOME/GTK, not Compiz. I think a great solution would be if Nautilus generalized the problem by allowing custom backgrounds for all folders, not just the one 'Desktop'. Then you can have a unique desktop folder for each workspace, with its own background image (using symbolic links for files/folders you want on all workspaces). 

> Avant Window Navigator, which I think is in the repo's. If you find cairo-dock not to your taste or its flakey for you then AWN is your friend. It doesn't seem so configurable as cairo-dock, but some people find it more reliable than cairo-dock and it does do exactly what it says on the box...

The version of [[COLOR="Blue"]Awn[/COLOR]]("http://launchpad.net/awn") in the repos doesn't have any of the applets. Awn is just not the same without [Python / [[COLOR="Blue"]Vala[/COLOR]]("http://en.wikipedia.org/wiki/Vala_(programming_language)")] applets, such as

[LIST][*]Launcher/Taskmanager
[*]Awn Terminal
[*]Stacks
[*]Stack Plugger
[*]Volume Control
[*]Shiny Switcher
[*]Showdesktop
[*]Comics
[*]RTM (Remember the Milk)
[*]Weather[/LIST]

It's nice how the dock integrates with the window manager, allowing you to right-click on running programs to control their Windows (including moving them to another workspace). But I wish there were some GTK/Qt APIs, too, to give programs more control over their dock icons and context menus. I've seen it done once before (in Exaile), but I believe it works through D-Bus rather than the toolkit. I think the dock should be seen as part of the DE and warrants more than an inter-application message bus. I'd like to see those dock icons come alive with dynamic 3D graphics that reflect the current state of running apps.

I also use Screenlets, and there too I'd like to see some more integration with the dock. I wish it were common for OSS projects to merge, because I think it would be stellar if the APIs for Screenlets and Awn merged to make applets/screenlets dockable on the bar as clickable icons, dockable to a sidebar in medium size, or stuck to the desktop in large size, and launchable from a stacks applet on the bar.

P.S. I know all this talk of close integration and merging of projects in the Linux world is a pipe dream. It's just there are certain limits and barriers in a loosely coupled system unless you have tight cooperation on clear standards. Sometimes all I can see are the inconsistencies and  redundancies that emerge from poor cooperation and communication between projects, and then all I want is a good Cathedral (with me calling the shots, of course :)

---

### Post by XanTrax on 2008-07-09
> **borlosky said:**
> I was finally able to get all plugins working fine. Here's how I did it:

1: went to add/remove from Applications menu, removed all compiz related software

2: went to Synaptic package manager and COMPLETELY Removed ALL compiz related software

3: Followed steps located here: [http://www.xs4all.nl/~mgj1/compiz_git.htm](http://www.xs4all.nl/~mgj1/compiz_git.htm)

4: Logged out, then back in. all working fine now!!:KS (all my previous keybindings were saved however, so very little configuration was needed other than just checking the new options)

Ive tried all that and I still cant seem to find the sphere anywhere?

---

### Post by Saint Angeles on 2008-07-09
a month or 2 ago i downloaded the latest compiz from git. i use the cylinder instead of sphere:

---

### Post by borlosky on 2008-07-10
> **XanTrax said:**
> Ive tried all that and I still cant seem to find the sphere anywhere?

are you loading compiz-fusion icon and going to settings from there? forgot to mention, i had to setup compiz-fusion icon to run at start up, then go to settings manager from the icon to configure and get all effects to work.

---

### Post by XanTrax on 2008-07-10
> **borlosky said:**
> are you loading compiz-fusion icon and going to settings from there? forgot to mention, i had to setup compiz-fusion icon to run at start up, then go to settings manager from the icon to configure and get all effects to work.

Yes.  I am running compiz-fusion and then going to CCSM and looking everywhere for sphere and I can not find it.  Where exactly would it be?  The CCSM that comes from the compiz-git looks nothing different (even plugins available wise) than the normal compiz that comes with 8.04.  Maybe im just missing it and not seeing it?  Where is the option for the sphere?

---

### Post by borlosky on 2008-07-10
> **XanTrax said:**
> Yes.  I am running compiz-fusion and then going to CCSM and looking everywhere for sphere and I can not find it.  Where exactly would it be?  The CCSM that comes from the compiz-git looks nothing different (even plugins available wise) than the normal compiz that comes with 8.04.  Maybe im just missing it and not seeing it?  Where is the option for the sphere?

it should be pretty apparent where the options are in ccsm, you'd see the extra plugins along side existing ones

---

### Post by XanTrax on 2008-07-10
> **borlosky said:**
> it should be pretty apparent where the options are in ccsm, you'd see the extra plugins along side existing ones

Well, maybe you missed my question, where did _**you**_ find the option for the sphere? I could not find it anywhere.

---

### Post by XanTrax on 2008-07-10
Disregard.  I forgot I ran the update command last now and I now I have found it.  Silly me :p.

[http://ckozler.net/screens/laptop_sphere.png](http://ckozler.net/screens/laptop_sphere.png)

:).  Thank you everyone in here who helped!

---

### Post by borlosky on 2008-07-10
> **XanTrax said:**
> Disregard.  I forgot I ran the update command last now and I now I have found it.  Silly me :p.

[http://ckozler.net/screens/laptop_sphere.png](http://ckozler.net/screens/laptop_sphere.png)

:).  Thank you everyone in here who helped!

cool, always seems to be the 1 simple thing i forget that messes me up too, lol. glad i could help :-)

---

### Post by XanTrax on 2008-07-10
> **borlosky said:**
> cool, always seems to be the 1 simple thing i forget that messes me up too, lol. glad i could help :-)

:p.

I ran ccsm from command line and saw all the "Adding [...] plugin...Successful.".  Thats when I realized it would be there :p.

---

### Post by kaboodle_fish on 2008-07-12
> **DXM31 said:**
> If you get that working let us know.
I was able to get 3d back, but the other effects snow,... won't work even after I tried to reinstall the effects individually. 
I can see them and they are still set up the way I had them but I can't check them:confused:

[http://ubuntuforums.org/showthread.php?t=820802&highlight=atlantis](http://ubuntuforums.org/showthread.php?t=820802&highlight=atlantis)

The script is on page four and the instructions on page two 

Don't forget to correct the name to compizplugins**4**.sh from compizplugins.sh 

Then you can have the sphere/cylinder with atlantis/snow inside

---

### Post by chris4585 on 2008-07-13
well i've been enjoying the sphere for a while now, on hardy heron, my question is.  is it alright to add

deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

when i already have the sphere and stuff and everything does work.. no issues at all

i installed compiz with the sphere and all using just this repo, i didnt know there was another one that comes with it.  If i dont add the second repo will i have issues or missing something?  I'm sure its fine, i just want to know what does the repo that i dont have do/add? since i already have everything working *as it appears*

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

---

### Post by azer89 on 2008-07-13
> 
 Re: Spherical Cube ?
well i've been enjoying the sphere for a while now, on hardy heron, my question is. is it alright to add

deb-src [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main

when i already have the sphere and stuff and everything does work.. no issues at all

i installed compiz with the sphere and all using just this repo, i didnt know there was another one that comes with it. If i dont add the second repo will i have issues or missing something? I'm sure its fine, i just want to know what does the repo that i dont have do/add? since i already have everything working *as it appears*

deb [http://ppa.launchpad.net/compiz/ubuntu](http://ppa.launchpad.net/compiz/ubuntu) hardy main


thank man....
it's really solve my problem

---

### Post by chris4585 on 2008-07-13
> **azer89 said:**
> thank man....
it's really solve my problem

your welcome i suppose, what did i do? :D

---

### Post by Lexrst on 2008-07-29
> **16777216 said:**
> To use the repository addresses above just follow these simple steps.



Thanks!  Worked perfectly... (see attached)

-Lexrst

---

### Post by dark-_-blades on 2009-07-10
Guys, i need help :(

I am running hardy 64bit, and i've tried installing a new compiz fro launchpad repo. but the sphere didn't work at all. When i tried to install from git, i've uninstalled compiz and emerald, and when running
> ./compiz-git install
the last line looks like this:
> Pulling compiz from git... failed!

Please, i appreciate your help.

Rgds,
Shadowbane

---

