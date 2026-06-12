---
title: "Folder Colour not working in 22.04"
date: 2022-06-27
forum: General Help
---

### Post by BolinMDT on 2022-06-27
Hi all, I'm trying to change the colour of the standard Yaru folders from Grey to traditional yellow/beige/orange and so followed online instructions to install the Folder Colours extension.

The Folder Colour option will let me add labels to folders, but it doesn't change the colour when you select one (I have restarted the system).

Also, I have read about the 'Global Colour' option to change all folders, which is what I really want to do, but I can't see where to select that.

Any help greatly appreciated.

Thanks, Bolin

---

### Post by tea for one on 2022-06-28
> **BolinMDT said:**
>  so followed online instructions to install the Folder Colours extension.
Which instructions did you follow?

Alternatively, you could use Papirus Icons and Papirus Folders (where there is a choice of colours)
[https://github.com/PapirusDevelopmentTeam/papirus-icon-theme](https://github.com/PapirusDevelopmentTeam/papirus-icon-theme)
[https://github.com/PapirusDevelopmentTeam/papirus-folders](https://github.com/PapirusDevelopmentTeam/papirus-folders)

---

### Post by BolinMDT on 2022-06-28
I used the command lines from here:

[https://linuxhint.com/change-folder-color-ubuntu/](https://linuxhint.com/change-folder-color-ubuntu/)

I note that the Folder Color application doesn't appear in the Ubuntu Software centre, presumably there is a compatibility issue with 22.04? Yet I have found 2 or 3 articles online outlining steps to use it with 22.04:-k

Any ideas as to the issue? Maybe because I have Gnome Tweaks and Gnome Extensions installed?

Will check the out the Papirus icons, thanks.

---

### Post by tea for one on 2022-06-28
I installed the Folder Colour PPA and followed the linuxhint guide.
I changed my icons to a Yaru option and the Folder Colour did not work as you indicated in post 1

However, I then changed my icons back to Papirus and the Folder Colour choice worked. 
If I could offer an explanation, I would..............?

I also have gnome-tweaks and extensions installed but I do not think that this is pertinent.
Probably, something to do with hard-coding of Yaru themes/icons?

---

### Post by tea for one on 2022-06-28
I may have accidentally stumbled upon an answer.

Settings > Appearance > Change colour to Ubuntu Orange 
Then open Files (Nautilus) and see if the Folder Colour functions OK

---

### Post by BolinMDT on 2022-06-28
Yep, thank you, well done for spotting that, folder colour now changes OK as it should, and even remembers what it was last set to before reverting to the orange accent - the folder I had been trying it on automatically turned yellow upon changing back to orange accent.

Problem is I want the Olive accent and yellow folders! Erm.....?

I tried setting the accent to the default orange, changing the folder colours to yellow (which worked) and then changing the accent back to Olive but that automatically reverted the folders back to Grey/Olive.

Also I have read about the option to change the default colour for all folders, a 'global colour' option, but can't see any option for that?

---

### Post by tea for one on 2022-06-28
> **BolinMDT said:**
> Also I have read about the option to change the default colour for all folders, a 'global colour' option, but can't see any option for that?
Neither did I.

Papirus Folder Colour switcher will work globally.
Then via Folder Colour, you can change individual folders in your home directory independently of the global choice.

---

### Post by BolinMDT on 2022-06-28
Well I wasn't so keen on the Papirus icons, but managed to find another way around this.

I located the yellow folder icons in the Yaru icons 'places' folder, changed the permissions for the Yaru-olive icons 'places' folder from root to me and did some copying and pasting. This has worked perfectly (so far!) and only 2 or 3 icons are the grey type, but not ones I usually see anyway. The old icons are still in the folder with -bkup added to the filename, and backed up elsewhere just in case.


I can't see any issue with this solution so far.

Now to try to change the files icon in the dock...

---

### Post by BolinMDT on 2022-06-28
Files icon in the doc sorted this was the one in the 256x256 folder, again changed the permissions, copied and opened in GIMP, changed the grey to yellow and replaced with the grey/olive kept as a back-up.

So all sorted to my satisfaction.

Not sure if this topic should be marked as SOLVED or not? I found my own way around the problem, but the actual problem is that if you choose an different accent colour from default orange then the 'Folder's Colour' extension doesn't change the colour (but will change the label).

It seems that the extension puts the coloured set of folders into the Yaru icons places folder but not into the other Yaru accents' icons places folders, and if another accent is chosen then the folder icons are taken from the places folder of the 'Yaru-(alternative accent), hence the extension doesn't take effect. Hope that makes sense.

---

### Post by Claus7 on 2022-06-28
Hello,

Nice that you were able to solve your issue. I have to admit that I haven't completely understood the changes you applied. A photo before and (actually) after could have been more informative I suppose.

Even a little bit late you could check this link:
[https://www.gnome-look.org/p/1012504](https://www.gnome-look.org/p/1012504)
it has many different colors of icons to choose from and you could copy them under /usr/share/icons for global changes. In order for these to take effect I think that you should first log out and then log in again. 
Just as an alternative, which might be to your liking.

Regards!

---

### Post by BolinMDT on 2022-06-30
I did take a screenshot but currently my limited online pgoto hosting is full and didn't want to sort another just that - apologies. But the changes were simple.

I worked out that the folder icons were being taken from /usr/share/icons/Yaru-olive/48x48/places with Yaru olive accent colour and small folder icons selected under settings. The coloured folders were saved by the 'Folder's Color' extension in /usr/share/icons/Yaru/48x48/places. After changing the ownership of /usr/share/icons/Yaru-olive/48x48/places in the terminal to myself, I then copied the Yaru olive icons, adding -bkup to the name of the copies, saving them in the same folder as the originals. I then copied the yellow icons from usr/share/icons/Yaru/48x48/places into /usr/share/icons/Yaru-olive/48x48/places, replacing the originals. Additionally I then copied the standard folder icon twice, and renamed as user-home and as user-desktop, so those icons are the standard folder icon not the special icon, but are the correct colour, as there were no yellow versions of these. I left the original grey/olive folder-remote, folder-dropbox, insync-folder and preferences-desktop-wallpaper icons as they were (without back-ups) as I rarely/never see these and there were no yellow versions of these either. I then changed the ownership of /usr/share/icons/Yaru-olive/48x48/places back to root in the terminal.

For the Files icon in the dock, I found the icon in  /usr/share/icons/Yaru-olive/<SIZE>/apps and changed the ownership of a couple of different sized folders, swapping the Yaru olive icon for the standard icon, to see which size icon the dock was using. It turned out to be 256x256. I copied it to desktop, changed the grey colour to yellow with GIMP, pasted back into /usr/share/icons/Yaru-olive/256x256/apps, restarted the system to check it worked correctly, and changed the ownership of the folders I had changed to myself  back to root.

I did look at several sets of icons in gnome-look first, but really wanted to keep the standard Yaru icons with yellow folders as my preference, hence I came up with this way of doing that.:)

---

