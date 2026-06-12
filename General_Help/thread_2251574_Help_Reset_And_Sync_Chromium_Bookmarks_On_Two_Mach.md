---
title: "Help Reset And Sync Chromium Bookmarks On Two Machines"
date: 2014-11-05
forum: General Help
---

### Post by Smallwheels on 2014-11-05
I just bought a new laptop running Chrome OS. I'm on a Linux machine. I want my best bookmarks list to be synchronized between the old machine and the new one. The bookmarks that automatically transferred to the new machine using sync are a really old configuration. I've tried a few things including resetting the bookmarks on the original machine but the new machine's bookmarks (which is the old list) took precident over the old machine, and thus the old machine loaded an old list of bookmarks. 

To combat this and totally start anew I have saved the bookmarks I want in an HTML file. Then I deleted Chromium on the Linux machine and reloaded it. Unfortunately when it reloaded, it loaded a bookmarks file from the Linux machine that were stored somewhere.

What I need to know is where is that file and how do I delete it? When I uninstall and reinstall Chromium it should have no bookmarks added automatically. I will then load the HTML file of bookmarks that I want. Then I will reset the new machine so that it doesn't have the unwanted bookmarks list on it. 

If I do this it is my hope that since there will be no record of the old bookmarks list, the new one can be loaded and both machines will then be synchronized with the bookmarks I want. Does this make sense? 

Where is the Chromium bookmarks file that didn't get deleted when I uninstalled it? That is what I need to find. 

If you recognize something I'm doing wrong or am not doing at all please correct me. 

Thank you. Your experience and knowledge is appreciated.

---

### Post by westie457 on 2014-11-05
Hello smallwheels, on a linux machine the saved bookmarks file should be in either the '.cache' or the '.config' folder. On ChromeOS it will possibly be in a similar location.

In Chromium and Google Chrome browsers it is possible to sync lots of things including Bookmarks to your Google account.

If you have not already set up 'Sync' in Chromium you should be able to manually delete the unwanted items from the bookmarks folder then click on the icon top right > Sign into Google. From there you should be offered a chance to sync various things and/or everything.

Anything you are not sure of post back.

---

### Post by Smallwheels on 2014-11-05
Thank you westie457. What is the path to find the .cache or the .config folders? Should I just delete the whole folder? If I knew all of the things to uninstall I could manually do it after uninstalling Chromium. This would ensure it was all gone. 

Wouldn't it be good if within the sync feature one could select which computer had the master list at original syncing time? This way the inferior list on one machine couldn't possibly be selected and override the desired list.

---

### Post by Mike_Walsh on 2014-11-05
Hi, Smallwheels.

If I was in your situation, I would first make sure that I had a copy of the bookmarks you want to use saved in a safe location. Then, I would go into 'Settings' in Chromium, and choose 'Disconnect your Google account'. 

Once that was done, I would then uninstall Chromium. I would go into Nautilus, select 'Hidden Files' in your 'Home' folder, and delete the entire '.chromium' folder. Then re-boot.

When your machine is back up & running, you can then re-install Chromium. Since you've deleted the .chromium folder, it will have to be re-created from scratch, without your old bookmarks. This being the case, you can then re-install your preferred bookmarks list.

As I don't know anything about ChromeOS, I am guessing you'll need to follow Westie's advice, and attempt to delete the bookmarks from the ChromeOS browser. In the normal course of things, I would want to disconnect the account on the ChromeOS machine, too, so that you'd be starting with a clean slate on both machines. Having reinstalled your bookmarks on your Linux machine, you SHOULD then find that when you sign-in on the ChromeOS machine, it ought to sync with the desired bookmark list from the Linux machine.....fingers crossed!

This is, of course, all assuming that you haven't got any other machines with old Chrome/Chromium bookmarks knocking about the place anywhere!

Hope this is of some use. It's only a suggestion of course, but give both it and Westie's suggestion a try, please, and let us know how you get on. ;)

Regards,

Mike.

---

### Post by Smallwheels on 2014-11-05
Mike_Walsh thank you. I went to my root folder seeking the Chromium folder and it gives the message "This does not belong to you. You don't have permission to view this folder". Until I can locate all of the folders to delete I can't proceed. There must be a way to access this folder in the command line. What would that command be?

Thank you.

---

### Post by Mike_Walsh on 2014-11-06
Hi, Smallwheels.

I think (and don't take this as gospel) that you have to open your home folder as root in order to be able to work with the hidden (or config) files. I can't really advise further, until I know which OS you're running, as the procedure varies slightly from one distro to another.....since they tend to use different file managers.

Let us know which OS you're running, and we'll take it from there.

Regards,

Mike.

EDIT: Curious. I've just tried accessing my Chromium and Google-Chrome config files in /home, and have no problems at all in doing so. BTW, I forgot to mention that once you've enabled 'Show hidden files', you need to go into 'config' to access them. Clicking on them should then take you straight into the respective folders. I haven't yet attempted to change anything, although for the life of me I can't locate the bookmarks database; will need to do a bit more research on that, I think.

---

### Post by ringstaart on 2014-11-06
Running "sudo apt-get purge chromium" in a terminal should also get rid of any configuration chromium leaves behind. You can use this for other programs too, if you have similar problems. After doing that, reinstall chromium.

By default, uninstalling a program only removes the program, and not the configuration. By running the above command, you "purge" the program, which means you remove every part of the program, including configuration.

---

### Post by Smallwheels on 2014-11-07
My version of GNU/Linux has been Elementary Luna for almost the whole year. It has worked OK so I haven't switched it. It is a version of Ubuntu 12.04 LTS. Learning to purge things in the command line is a really great tool. It saves time by not having to find folders and deleting them manually. I hope I can remember that one. I'll give it a try.

---

