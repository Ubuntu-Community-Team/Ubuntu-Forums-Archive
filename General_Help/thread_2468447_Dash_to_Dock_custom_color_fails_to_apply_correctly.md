---
title: "Dash to Dock custom color fails to apply correctly"
date: 2021-10-30
forum: General Help
---

### Post by Dennis N on 2021-10-30
Ubuntu 21.10. There's something weird going on with dash-to-dock. I am attempting to change the background color to one of my choice. The problem is, it changes, but never to the color I select. To illustrate, I chose yellow (screenshot 1). The background changed to pink instead. I logged out and in to see if that made a difference, and found my the color just reverts to the original dark gray (screenshot 2) even though yellow is still indicated. Can anyone confirm this bug, or find an error in my procedure?

Also, the "counter indicators" were chosen to be dots. They are still the little pointy things.

One other thing: if you look carefully, there is a black rectangle underlying the dock. That should not be there.

---

### Post by mIk3_08 on 2021-10-30
> **Dennis N said:**
> Ubuntu 21.10. There's something weird going on with dash-to-dock. I am attempting to change the background color to one of my choice. The problem is, it changes, but never to the color I select. To illustrate, I chose yellow (screenshot 1). The background changed to pink instead. I logged out and in to see if that made a difference, and found my the color just reverts to the original dark gray (screenshot 2) even though yellow is still indicated. Can anyone confirm this bug, or find an error in my procedure?
Also, the "counter indicators" were chosen to be dots. They are still the little pointy things.
One other thing: if you look carefully, there is a black rectangle underlying the dock. That should not be there.
Try using some app like gnome tweak tool. This might give you a help. Or you can just try to use the transparency leveled low so that the color of your dock will blend to the color of your wallpaper and its cool to the eye. But if you want the color of your choice just use some tweak apps. 
To install some gnome tweak here are the command below or you can just use the Ubuntu Software App to install the application you want. Good Luck.
```
sudo apt install gnome-tweaks
```

---

### Post by Dennis N on 2021-10-30
> **mIk3_08 said:**
> Try using some app like gnome tweak tool. This might give you a help. Or you can just try to use the transparency leveled low so that the color of your dock will blend to the color of your wallpaper and its cool to the eye. But if you want the color of your choice just use some tweak apps. 
To install some gnome tweak here are the command below or you can just use the Ubuntu Software App to install the application you want. Good Luck.
```
sudo apt install gnome-tweaks
```

Thanks for the reply. 

Unfortunately, we can't set the dash to dock transparency in Ubuntu 21.10 at all. That setting not is functional. The Tweaks tool no longer deals with Gnome shell extensions - that job is now done with the Extensions app. 

It is possible to use the default settings for appearance, but the customizations should function. With the default settings, the dock is solid black, and the other problems mentioned - underlying dark gray rectangle and that of the counter indicators also exist under the defaults.
 
Ubuntu may intend the user to use Ubuntu Dock, not install Dash to Dock. If indeed these are bugs, it may be the extension's maintainer, not Ubuntu, that needs to fix this for Gnome 40. 

I'm still looking for confirmation from another user of Ubuntu 21.10 who would check Dash to Dock for these problems.

---

### Post by tea for one on 2021-10-30
@ Dennis N 

Yes, something weird about Dash to Dock.

I'm not a regular user of this extension but I tried it after reading your post.

My findings are:-

Background colour changed once successfully and then regularly failed to change.
Black rectangle under dock is visible
Panel Mode: extend to screen edge makes it less visible.
Window Counter indicator is OK with dots (and change to other styles seems fine)

Back to Dash to Panel now ;)

Edit: Some issues (among others) reported  about colour/transparency  here [https://github.com/micheleg/dash-to-dock/issues](https://github.com/micheleg/dash-to-dock/issues)

---

### Post by monkeybrain20122 on 2021-10-30
Hi, maybe you want to use Dash to Panel instead. D to D's support for gnome 40 has been broken for a while and I think it just got fixed in Oct.  D to P has been working great though (screenshot from Archlinux and gnome 40. but I think it works the same way on Ubuntu)

---

### Post by mIk3_08 on 2021-10-31
> **Dennis N said:**
> Gnome Tweaks tool. Yeah. Actually, I don't really use this tool. But maybe this will run on Linux Ubuntu 21.04 Hirsute Hippo.
They have a list of new version according to the new Linux Ubuntu Operating System release. Maybe this will help. [Click here.]("https://www.ubuntuupdates.org/pm/gnome-tweak-tool")

---

### Post by Dennis N on 2021-10-31
> **tea for one said:**
> @ Dennis N 

Yes, something weird about Dash to Dock. I'm not a regular user of this extension but I tried it after reading your post.
My findings are:-

Background colour changed once successfully and then regularly failed to change.
Black rectangle under dock is visible
Panel Mode: extend to screen edge makes it less visible.
Window Counter indicator is OK with dots (and change to other styles seems fine)

Back to Dash to Panel now ;)

Edit: Some issues (among others) reported  about colour/transparency  here [https://github.com/micheleg/dash-to-dock/issues](https://github.com/micheleg/dash-to-dock/issues)

Thanks for taking the time to test and confirming the problems. That helps. I also found it's appearance varies with the gnome shell theme being used. But all that I checked have the background color problem and none have transparency. The counters will change in some themes, not others. 

Since the dash to dock is independent of Gnome and Ubuntu, I guess it is really up to the creator of the extension to fix any bugs.

---

### Post by Dennis N on 2021-10-31
> **monkeybrain20122 said:**
> Hi, maybe you want to use Dash to Panel instead. D to D's support for gnome 40 has been broken for a while and I think it just got fixed in Oct.  D to P has been working great though (screenshot from Archlinux and gnome 40. but I think it works the same way on Ubuntu)

That's a good option to consider. I am also thinking of Plank, which can stay on the left and has a lot of configurations possible. Plank won't work with Wayland, but I use Xorg (for now) so it would be ok. I use it now on Xubuntu.

---

### Post by Dennis N on 2021-10-31
> **mIk3_08 said:**
> Yeah. Actually, I don't really use this tool. But maybe this will run on Linux Ubuntu 21.04 Hirsute Hippo.
They have a list of new version according to the new Linux Ubuntu Operating System release. Maybe this will help. [Click here.]("https://www.ubuntuupdates.org/pm/gnome-tweak-tool")

Yes, I used it on 21.04 and it's installable on 21.10 too. It's just that the "Extensions" choice has been removed from the left panel of Tweaks, so it can't be used for managing the gnome-shell extensions any longer. It's still a great tool for the other categories.

---

### Post by Dennis N on 2021-11-01
> **monkeybrain20122 said:**
> Hi, maybe you want to use Dash to Panel instead. D to D's support for gnome 40 has been broken for a while and I think it just got fixed in Oct.  D to P has been working great though (screenshot from Archlinux and gnome 40. but I think it works the same way on Ubuntu)

I have given Dash to Panel a try. It seems to have its own problems. I found the "Show Applications" icon on the far left of the panel does not display the application grid, just am empty overview. (see screenshot). This is a bug:

[Failure of "Show Applications" button on panel.]("https://github.com/home-sweet-gnome/dash-to-panel/issues/1489")

The author will need to offer an upgrade. On the other hand, it's possible to change the color, which dash to dock cannot do. Opacity does not seem to work in either one. 

I am back using Dash to Dock on this machine, skipping the customization now, but I'm also trying out Plank on a second Ubuntu 21.10. It looks very promising.

---

### Post by monkeybrain20122 on 2021-11-01
> **Dennis N said:**
> I have given Dash to Panel a try. It seems to have its own problems. I found the "Show Applications" icon on the far left of the panel does not display the application grid, just am empty overview. (see screenshot). This is a bug:

[Failure of "Show Applications" button on panel.]("https://github.com/home-sweet-gnome/dash-to-panel/issues/1489")

The author will need to offer an upgrade. On the other hand, it's possible to change the color, which dash to dock cannot do. Opacity does not seem to work in either one. 

I am back using Dash to Dock on this machine, skipping the customization now, but I'm also trying out Plank on a second Ubuntu 21.10. It looks very promising.

Interesting. What is the gnome shell version in Ubuntu 21.10? I saw that on Arch too when gnome shell updated to 40.4.1, I downgraded it back to 40.3.1 and pinned the package and that solved my problem so I never thought about it since (in  Arch you can downgrade packages, that is a very cool feature) I thought that was a gnome-shell issue and just left it at that, now with your links it turns out to be a dash to panel bug..

---

### Post by tea for one on 2021-11-01
> **Dennis N said:**
> I have given Dash to Panel a try. It seems to have its own problems. I found the "Show Applications" icon on the far left of the panel does not display the application grid, just am empty overview. (see screenshot). This is a bug

Yes, there is a dilemma with the overview grid being empty but there is a fix.
You have to download and build the extension from github.
Unfortunately, I can't remember [COLOR="#0000FF"]exactly[/COLOR] the procedure.
First, remove the existing Dash to Panel extension.

```
sudo apt install git
git clone https://github.com/home-sweet-gnome/dash-to-panel.git
cd dash-to-panel
sudo apt install make
make install

```

Somehow, I managed it but not necessarily as the order of the above commands.
Screenshot attached

Hopefully, the extension will be fine by the time 22.04 LTS arrives - fingers crossed.

---

### Post by Dennis N on 2021-11-01
> **monkeybrain20122 said:**
> Interesting. What is the gnome shell version in Ubuntu 21.10? I saw that on Arch too when gnome shell updated to 40.4.1, I downgraded it back to 40.3.1 and pinned the package and that solved my problem so I never thought about it since (in  Arch you can downgrade packages, that is a very cool feature) I thought that was a gnome-shell issue and just left it at that, now with your links it turns out to be a dash to panel bug..

Here's the current gnome-shell version:
```
dmn@Tyana-vm:~$ gnome-shell --version
GNOME Shell 40.5

```

On Dash to Panel, is it normal for the Gnome Dash to appear on the Activities Overview along with Dash to Panel? See screenshot in Post #10. I would expect the Dash to be hidden as it is when Dash to Dock is in use. See the screenshot below.

---

### Post by Dennis N on 2021-11-01
> **tea for one said:**
> Yes, there is a dilemma with the overview grid being empty but there is a fix.
You have to download and build the extension from github.
...
Hopefully, the extension will be fine by the time 22.04 LTS arrives - fingers crossed.

Thanks, let's hope so. Rather than try to build it, I'm going to just wait and see. Extensions are frequently upgraded even within the current release. The Dash to Dock is usable and doesn't look that bad provided you don't use any customizations and you select a compatable gnome shell theme. There is a screenshot in post #13 of the Activities Overview and what I have now.

---

### Post by monkeybrain20122 on 2021-11-02
> **Dennis N said:**
> 

On Dash to Panel, is it normal for the Gnome Dash to appear on the Activities Overview along with Dash to Panel? See screenshot in Post #10. I would expect the Dash to be hidden as it is when Dash to Dock is in use. See the screenshot below.

Hi, the dash can be configure to show or hide. I think the default should be hidden. See the settings:

---

### Post by Dennis N on 2021-11-02
> **monkeybrain20122 said:**
> Hi, the dash can be configure to show or hide. I think the default should be hidden. See the settings:
OK, I see that setting now and changed it. Thanks.
I also notice that Dash to Panel &#8595; does have transparency working. In post #10, I thought it didn't.

---

### Post by monkeybrain20122 on 2021-11-02
> **Dennis N said:**
> OK, I see that setting now and changed it. Thanks.
I also notice that Dash to Panel &#8595; does have transparency working. In post #10, I thought it didn't.


So did you get transparency to work? According to this [link]("https://github.com/home-sweet-gnome/dash-to-panel/issues/1437#issuecomment-902875910"), the patch restored show applications but broke transparency (see last three posts)

---

### Post by Dennis N on 2021-11-02
> **monkeybrain20122 said:**
> So did you get transparency to work? According to this [link]("https://github.com/home-sweet-gnome/dash-to-panel/issues/1437#issuecomment-902875910"), the patch restored show applications but broke transparency (see last three posts)

Yes, It works. Look at the Panel in post #16 screenshot. Its darker on the left and lighter on the right. It is transparent to the background image's color variation. It suppose it's because I didn't install a patch. So, the "Show Applications" still doesn't work here. But, you can just use the Applications Menu on the panel if you need to locate some application to use.

---

### Post by Dennis N on 2021-11-02
Since Dash to Panel is just an extension for the panel, wouldn't it's transparency depend on the panel's ability to have transparency? The gnome-shell theme in post #16 has a transparent panel. Maybe that's why transparency works. It seems logical.

Two other shots showing Plank as a Dash-to-Dock substitute attached. I like it too. Here it's set to be partly transparent. Note on the Overview, Plank won't appear - instead, the Gnome Dash appears. It only works with Xorg, not Wayland.

---

