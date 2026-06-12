---
title: "Updateing Zoom on Ubuntu"
date: 2023-02-09
forum: General Help
---

### Post by Tom_Carr on 2023-02-09
Do I need to do anything special to update Zoom, or does it update automatically?

---

### Post by grahammechanical on 2023-02-09
It depends on whether you are using the snap packaged version or the deb packaged version. I have zoom-client installed as a snap packaged version and it receives automatic updates because the snap package is maintained by a Canonical engineer. The snap packaged version of Zoom-client is presently at version 5.13.4.7.11. The deb packaged version which we get from the zoom donnload page is at 5.13.7.

If I remember correctly, to update the deb packaged version we download the latest version from the zoom download page, uninstall the existing version of zoom and the install the newer version.

Regards

---

### Post by Tom_Carr on 2023-02-09
I installed Zoom from the ubuntu software app.  That is the only way I know how to install stuff.  I am a light weight user.

---

### Post by mIk3_08 on 2023-02-10
> **Tom_Carr said:**
> I installed Zoom from the ubuntu software app.  That is the only way I know how to install stuff.  I am a light weight user.
Based on what I observed to my 22.04 LTS desktop Ubuntu Software will notify when Ubuntu Software detect a new update to an application. It will show directly to the Updates tab on Ubuntu Software. See image below. Regards and cheers
[IMG]https://ubuntuforums.org/attachment.php?attachmentid=291739&stc=1[/IMG]

---

### Post by Paddy Landau on 2023-02-10
To add to what was already stated, anything that you install from the Software Store will be automatically updated when it becomes available.

However, you have to depend on Canonical to provide those updates!

Generally, updates are given only for security problems (because Canonical tries to keep things stable rather than state-of-the-art), but there are exceptions. Zoom is one of them, although it's not kept to the very latest version but might lag somewhat.

If you *need* the very latest, you can use either the DEB (from the official website) or flatpak, but that requires further knowledge. Please ask if you need to know, and we'll help.

One extra point: If you are a "lightweight" user, please stick to the LTS versions of Ubuntu. The latest one is 22.04, and the next one will be 24.04. The other versions are short-term releases and should be treated as experimental. (If you already have 22.10, be sure to keep upgrading when a new version of Ubuntu is released, until 24.04.)
> **grahammechanical said:**
> The snap packaged version of Zoom-client is presently at version 5.13.4.7.11.
Curiously, for me, the snap version is 5.13.3.651, a bit behind yours. I wonder if snap packages are phased?

The flatpak version is at 5.13.7.683, the same as on the official website.

---

### Post by Tadaen_Sylvermane on 2023-02-10
> [COLOR=#000000]If I remember correctly, to update the deb packaged version we download the latest version from the zoom download page, uninstall the existing version of zoom and the install the newer version.[/COLOR]

Still accurate. Last I used the .deb installer it didn't put anything in my sources.list(.d/*). So it was a manual chore to go to the site, check version number, and update if needed. I switched to the flatpak for the reasons Paddy mentioned just before my post here. It's been current near immediately after zoom updates the .deb.

*EDIT* I suppose if one was so inclined they could write a scraper to check the site daily for an update and wget it but that is out of range for most of us I imagine.

---

### Post by Tom_Carr on 2023-02-10
> [COLOR=#000000]One extra point: If you are a "lightweight" user, please stick to the LTS versions of Ubuntu. [/COLOR]

That's what I do.  I upgrade every 2 years.

> [COLOR=#000000]anything that you install from the Software Store will be automatically updated when it becomes available.[/COLOR]

OK, I guess I don't really need to do anything then.

---

### Post by Paddy Landau on 2023-02-10
> **Tom_Carr said:**
> That's what I do. I upgrade every 2 years.
Yes, me too! I've been going since version 8.04. Goodness, that's 15½ years already! Time flies when you're having fun :)
> **Tom_Carr said:**
> OK, I guess I don't really need to do anything then.
Indeed, no. Ubuntu was designed to be as easy as possible for non-technical people.

You need worry only if you get a serious issue with Zoom that an update would fix, but then the person who packages Zoom on snap would most likely attend to it within 24 hours anyway. It's an unlikely scenario.

---

### Post by monkeybrain20122 on 2023-02-10
Or you can try this unofficial apt repo at your own risk

[https://github.com/mwt/zoom-apt-repo](https://github.com/mwt/zoom-apt-repo)

> Zoom does not provide an official repository for Debian/Ubuntu. This repository serves the latest official .deb from Zoom. All files are checked against the Zoom GPG keys. The repo is automatically updated twice per day.

---

### Post by grahammechanical on 2023-02-12
> I installed Zoom from the ubuntu software app.  That is the only way I know how to install stuff.  I am a light weight user.                 

It most likely is the snap packaged version. To check, open Ubuntu Software and find the zoom-client page. In the top panel you will see Source. It should say Snap Store (Snap). Open the drop down menu and you will see Latest/Stable; Latest/Candidate; Latest/Beta and Latest/Edge. Which one do you have ticked? I am on the Latest/Edge. So, it is the newest snap version.

Snap packages are not phased but we do have a choice of "channels."

By the way, on the Ubuntu Software zoom-client page you will a box labelled Permissions. Open Permissions and you can make some changes to the permissions that zoom-client is given.

Also, the rubbish bin icon will uninstall the snap packaged version of zoom-client.

Regards

---

### Post by freesitebuilder on 2023-03-24
I'm also having update problems with Zoom. Ubuntu software shows my installed version is 5.13, an "unofficial repackage of the Debian package" - I installed from Zoom website as at the time it wasn't available in Software. When I run, it shows as an older version (5.8), and won't let me join meetings as it's too old. Activities shows two Zoom icon - one with the camera icon, and one with just the word "zoom" on a blue background. The one that loads is the camera icon - the other, which appeared recently, doesn't seem to do anything. Settings shows choices for the new icon, the app with the camera icon has no options in settings. 

Yesterday I couldn't even load from the website - it just asked me which app I wanted to load. I assume one is .deb and one is snap - don't know how I've got two!
Ubuntu 22.04LTS

---

### Post by Paddy Landau on 2023-03-24
> **freesitebuilder said:**
> … [COLOR=#000000]don't know how I've got two![/COLOR]
The snap version of Zoom is 5.13.3.651.
The DEB version is 5.14.0 (1720).
The flatpak version is 5.13.11.1288.

To uninstall the DEB version:
```
sudo apt remove zoom-client
```
To uninstall the snap version:
```
sudo snap remove zoom-client
```
To uninstall the flatpak version:
```
flatpak uninstall us.zoom.Zoom
```

---

### Post by freesitebuilder on 2023-03-24
So, trying to remove deb tells me there isn't one - do I mean snap? 
Loading the snap gives me a login screen showing v5.8, logging in tells me I need to update to at least 5.10, and takes me to the download site at Zoom - deb v5.14 but I have snap.
Snap store shows the one I have installed.

I think online meetings are vastly over-rated anyway! Sadly I do need to use Zoom for a couple of volunteer online meets.

---

### Post by zebra2 on 2023-03-24
Download and rename the zoom update deb file to your home folder.  Sudo apt-get install ~/zoom.deb. You are updated.

---

### Post by Paddy Landau on 2023-03-24
> **freesitebuilder said:**
> So, trying to remove deb tells me there isn't one - do I mean snap? 
Loading the snap gives me a login screen showing v5.8, logging in tells me I need to update to at least 5.10, and takes me to the download site at Zoom - deb v5.14 but I have snap.
Snap store shows the one I have installed.
This is a little confusing, because the snap store's version is definitely 5.13, not 5.8. Unless you are confusing the snap store with the Ubuntu store? They're not the same thing.

If you don't have a DEB version installed, I wonder if you have at some point manually installed it instead of going through the store? Or, maybe, you downloaded the [appimage version]("https://appimage.github.io/Zoom/") and have never updated it since?

Do you have flatpak?

Enter these three commands and post the results of each.
```
apt list --installed 'zoom*'
snap list | grep zoom
which zoom-client
```
We can decide how to proceed from there.
> **zebra2 said:**
> Download and rename the zoom update deb file to your home folder.  Sudo apt-get install ~/zoom.deb. You are updated.
Why do you need to rename the DEB file? This way might work, but it's probably best to get rid of the existing old runtime first.

---

### Post by zebra2 on 2023-03-24
> **Paddy Landau said:**
> 
Why do you need to rename the DEB file? This way might work, but it's probably best to get rid of the existing old runtime first.
I've been using zoom for years and a install is as good as an update.  I rename the file because I copy it to several systems and I can reuse the command line. Simple!

---

### Post by freesitebuilder on 2023-03-25
apt list gives:
zoom /now 5.8.4.210 amd64 [installed, local]

snap list gives:
zoom-client 5.13.3.651

which zoom-client gives:
/snap/bin/zoom-client

---

### Post by Paddy Landau on 2023-03-25
> **freesitebuilder said:**
> ```
zoom /now 5.8.4.210 amd64 [installed, local]
```
Good, that gives us something to work on.

Let's get rid of this ancient version, which looks as though it had been manually installed, perhaps from the Zoom website:
```
sudo apt remove zoom
```
Next…
> **freesitebuilder said:**
> ```
zoom-client 5.13.3.651
/snap/bin/zoom-client
```
So, the snap version is correct. It's slightly out of date, but not by much; snap packages often are.

It should work now that you've uninstalled the apt version. If it's unavailable from the menu, reinstall Zoom as follows:
```
sudo snap remove zoom-client
sudo snap install zoom-client
```
Let us know how it goes.

---

### Post by deadflowr on 2023-03-25
The snap packages hasn't had a stable channel update in over two months.
If you want a more up-to-date version of the snap then change channels.
Currently the latest/edge channel has 5.14.0.1720.
```
snap install zoom-client --channel=latest/edge
```or if already installed
```
snap refresh zoom-client --channel=latest/edge
```

Note that the edge channel is typically considered more bleeding edge,
so

[list=1][*] It'll get a higher frequency of updates than the normal stable channels would.
[*] It'll have a chance of a higher frequency of issues because of the higher frequency of updates..
[/list]
If the edge channel does cause issues you can simply revert back to the stable channel.
```
snap refresh zoom-client --channel=latest/stable
```
If for some reason reverting fails you can simply do a snap remove of the package and install again.
The default install will always be for the stable channel unless you tell it otherwise.

More on channels here:
[https://snapcraft.io/docs/channels]("https://snapcraft.io/docs/channels")

---

### Post by Paddy Landau on 2023-03-25
@deadflowr: How do you see which channels are available for a specific app, e.g. zoom-client?

EDIT: I missed your link to the documentation. The answer is there.

---

### Post by deadflowr on 2023-03-25
> **Paddy Landau said:**
> @deadflowr: How do you see which channels are available for a specific app, e.g. zoom-client?

snap info <snap-package-name>
The bottom of the output will show what channels are available and what version of the package each channel is and when it was last updated.
Among other things.

---

### Post by Paddy Landau on 2023-03-25
> **deadflowr said:**
> snap info <snap-package-name>
Thank you. I had missed your link to the documentation, and that is useful.

---

### Post by deadflowr on 2023-03-25
I guess a new workaround if you want to try the bleeding edge channels but do not want to deal with possibly update breakages or issues you can put a hold on the snap until you feel like updating it.
Snapd introduced a new hold feature that allows holding a snap back from getting refreshed indefinitely, or until you want to unhold it.
to hold a snap simply run
```
snap resfresh --hold <snap-package-name-here>
```
to unhold
```
snap resfresh --unhold <snap-package-name-here>
```
If you run the -snap refresh --hold command without any packages it will put a hold on all installed snaps.
More: [https://snapcraft.io/docs/keeping-snaps-up-to-date#heading--hold]("https://snapcraft.io/docs/keeping-snaps-up-to-date#heading--hold")

For what it's worth.
Just throwing this out there.

Probably helpful if you don't trust an update or something.
Or if you like a very specific version and don't want to update it if you don't have to.
or any number of reason you might not want a package updated.


Edit: i see upon re-reading the doc for refresh holds that if you set a hold you can still update the package if you specify it.
But snap's auto-update feature will not update it. (as well as the general non-package-specific snap refresh command)
I guess that can be helpful if you dislike the randomness of snap auto-updates.

Sorry for the meandering random thoughts.

---

### Post by Paddy Landau on 2023-03-25
> **deadflowr said:**
> I guess a new workaround if you want to try the bleeding edge channels…
From what I can gather about the initiating question ([comment #11]("https://ubuntuforums.org/showthread.php?t=2483817&p=14136118&viewfull=1#post14136118")), the OP doesn't need cutting-edge, but 5.8 is just too old. Version 5.13 should be fine.

---

### Post by freesitebuilder on 2023-03-26
I've removed the .deb, so at least now the website loads. Did a remove and install of the snap version.  Software manager shows it's installed, safe, version 5.13. It's available in Activities menu, but clicking the icon does nothing - I used to  get the icon in the top bar, which I could then use to access the login pop-up.

---

### Post by Paddy Landau on 2023-03-26
> **freesitebuilder said:**
> I've removed the .deb, so at least now the website loads. Did a remove and install of the snap version.  Software manager shows it's installed, safe, version 5.13. It's available in Activities menu, but clicking the icon does nothing - I used to  get the icon in the top bar, which I could then use to access the login pop-up.
That's strange. It works perfectly on mine.

OK, let's try something a little different. This will sign you out of Zoom, so you'll have to sign in again. The next two commands not only uninstall Zoom, but also delete the associated data. Please take care to enter the commands correctly; in particular, the second command must be exactly as typed (you can cut-and-copy).
```
sudo snap remove --purge zoom-client
rm --recursive ~/snap/zoom-client
```
At this point, check if you still have access to Zoom. You shouldn't, but check anyway if it's in your menu.

If you do still have Zoom on your system, enter this command and give me the results.
```
which zoom-client
```
However, if it looks as though Zoom has been completely removed, reinstall Zoom:
```
sudo snap install zoom-client
```
Then try again.

If you still have problems, let us know which version of Ubuntu you're running. If you're unsure, post the results of this command.
```
lsb_release --all
```

---

### Post by freesitebuilder on 2023-03-26
Removed and checked it wasn't there, then re-installed. The icon is available in Activities but clicking just shuts down the menu with no sign of Zoom in the top bar or in the left hand menu.

I'm running 22.04.2 LTS.

---

### Post by freesitebuilder on 2023-03-26
Removed and checked it wasn't there, then re-installed. The icon is available in Activities but clicking just shuts down the menu with no sign of Zoom in the top bar or in the left hand menu.

I'm running 22.04.2 LTS.

---

### Post by Paddy Landau on 2023-03-26
> **freesitebuilder said:**
> Removed and checked it wasn't there, then re-installed. The icon is available in Activities but clicking just shuts down the menu with no sign of Zoom in the top bar or in the left hand menu.

I'm running 22.04.2 LTS.
This is strange. All right, let's investigate.

First, check whether or not Zoom is actually running.
```
ps -e | grep zoom
```
[SIZE=4]Case 1[/SIZE]

If this shows no results, it means that Zoom didn't actually start. In that case, run this command:
```
snap run zoom-client
```
What happens?

[SIZE=4]Case 2[/SIZE]

In this case, Zoom has started, but you can't see it. I'm hoping that it isn't Case 2, but let me know if it is and we'll go from there!

---

### Post by freesitebuilder on 2023-03-27
No results when checking if zoom is running. Running from terminal gives:

Testing for explicit PulseAudio choice...
... and PulseAudio has been explicitly chosen, so using it

---

### Post by Paddy Landau on 2023-03-27
> **freesitebuilder said:**
> No results when checking if zoom is running. Running from terminal gives:

Testing for explicit PulseAudio choice...
... and PulseAudio has been explicitly chosen, so using it
And then nothing else happens? That indicates to me that Zoom is running, but somehow it's invisible to you. I can't understand why this is happening, because I get the same terminal message as you do, and then Zoom opens fine.

I have three suggestions.

**First**

Try what @deadflowr suggested, which is to upgrade to the "edge" version:
```
sudo snap refresh zoom-client --channel=latest/edge
```
However, on my system, it didn't work; it is unable to install the latest/edge version of snap Zoom, even if I uninstall and reinstall.

To check if it worked, find which version you have installed with:
```
snap info zoom-client
```

**Second**

If that doesn't work, uninstall zoom completely and install the DEB version from the Zoom website.

[LIST=1]
[*]```
sudo snap remove --purge zoom-client
rm --recursive ~/snap/zoom-client
```
[*]Download the DEB from the [official website]("https://zoom.us/download").
[*]In the terminal, go to the directory where you downloaded the DEB and enter this command:
```
sudo apt install ./zoom_amd64.deb
```
[/LIST]
And then try again.

**Third**

If that *still* doesn't work, you might have to consider trying the flatpak version (this is what I usually use). If you want to do that and don't know how, ask.

Unfortunately, that is about the limit of where my knowledge ends, sorry about that. I hope that one of these solutions works for you.

---

### Post by freesitebuilder on 2023-03-28
Snap info shows installed version is 5.13, and at least I can join through the website by telling browser page to ignore any installed apps and load through the browser. Thanks for all the help - just another unsolved mystery that's beyond my understanding!

---

