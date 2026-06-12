---
title: "Wallpaper location and installation"
date: 2013-02-16
forum: General Help
---

### Post by ooleyguy on 2013-02-16
When I go to change my desktop background, I get a nice list of thumbnailed wallpapers. They include the stuff that was installed and some that I've gotten with Software Manager and Tweak Ubuntu.

My question is this: How do I get my wallpapers to go in with those "official" wallpapers. I move them to the proper directory but they still don't show up. I log out. I reboot. Still nothing.

Its the same with fonts. I can copy fonts to /usr/share/fonts all day, but none of them ever show up in applications unless I put them in ~/.fonts and that doesn't work well because then those fonts are only available to me. I know they are small files, but why should I have to make 4 copies of a font file and put them in each of the users home directories for everyone to use them?

---

### Post by Bufeu on 2013-02-16
This may help you: [http://askubuntu.com/questions/35759/how-do-i-set-another-search-directory-for-wallpapers](http://askubuntu.com/questions/35759/how-do-i-set-another-search-directory-for-wallpapers)

---

### Post by sudodus on 2013-02-16
I have installed wallpapers into the standard directory, and they are available. Maybe your wallpaper files have other permissions and ownership than those of the system.

Check with (use the real path, which is different between different flavours of Ubuntu)
for example
[FONT="Courier New"]/usr/share/lubuntu/wallpapers
/usr/share/wallpapers[/FONT]

```
ls -l /path-to-wallpapers
```
and change the permissions with [FONT="Courier New"][SIZE="3"]chmod[/SIZE][/FONT]
and change the ownership with [FONT="Courier New"][SIZE="3"]chown[/SIZE][/FONT]
if necessary.

This is the [FONT="Courier New"][SIZE="3"]ls -l[/SIZE][/FONT] output for a working wallpaper file
```
-rw-r--r-- 1 root root  209394 apr  5  2012 /usr/share/lubuntu/wallpapers/lubuntu-default-wallpaper.png
```

--
I don't know about copying fonts.

---

### Post by hawthornso23 on 2013-02-16
A little bit away from your question perhaps, but you might want to have a look at a wallpaper changer like wallch . You can point it at a folder or folders containing wallpaper and set it to change your wallpaper randomly every ten minutes or so.

---

### Post by ajgreeny on 2013-02-16
For font installation first make a folder to hold your own fonts. ```
sudo mkdir /usr/share/fonts/truetype/customttf
```  I am using customttf as an example.

Next open a terminal in the folder where you have a bunch of custom fonts and type ```
sudo cp ./*.ttf /usr/share/fonts/truetype/customttf
```  This will copy the truetype fonts to that folder.

Now that we have the fonts in the proper folder we need to install them in Ubuntu.  That is what the** fc-cache** command is for. Open a terminal in your customttf folder and type ```
sudo fc-cache -f -v
```This will install the fonts so that your applications like LibreOffice and others can use them.

I hope this helps.

---

### Post by ooleyguy on 2013-02-17
Excellent. Thank you all for your input. Coming from Windows, some of the ways to get stuff like this installed seems crazy. Using an XML file to determine where desktop wallpaper is located? Needing to use a command-line command to specify that you've installed a font where all the other fonts are and should be installed?

I love linux/Ubuntu, but whoever determined how some of these things works had to be high when they were doing the coding.

I won't even delve into the craziness that GRUB2 brings to mind.

---

### Post by sudodus on 2013-02-17
You wanted to install your pictures into the standard directory of backgrounds. So we helped you to do it.

But you need not do it that way. You can right-click on the desktop and use a GUI application to select a picture file to be the new background. As easy as in Windows.

---

### Post by PIE09gbLmgG6 on 2013-02-17
I found the right click option to work pretty well...although it started an issue for me regarding finding wallpaper I liked. I seriously haven't changed my wallpaper in 4-5 years...

Did get worried for a minute when trying to change it...but it worked easily...

Looking through some terragen landscapes...might find a nice one here soon...

ego-

---

### Post by ooleyguy on 2013-02-18
Yah, but it doesn't put that picture in the Wallpaper list making it look all official and stuff. I'm quite OCD when it comes to my computer and Ubuntu is making me crazy and feeding my OCD at the same time. There are places where the entire process seems chaotic, and other times where an OCD like me feels safe and secure in that little orderly womb.

---

