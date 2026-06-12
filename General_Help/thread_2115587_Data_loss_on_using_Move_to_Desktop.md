---
title: "Data loss on using Move to Desktop"
date: 2013-02-13
forum: General Help
---

### Post by simonbing on 2013-02-13
Background: two laptops, IBM T43s, one uses main hard drive for Win XP with a second hard drive in the Ultrabay slot running Ubuntu 12.04. Second T43 has Win XP but is wanting Ubuntu. I use the second Ultrabay hard drive in the first machine to back up the data in the second machine using an install live USB of Ubuntu. I just copy the the My Documents directory over to the Home directory in the Ultrabay slot. Then I remove the hard drive to install Ubuntu on the second machine as otherwise the Install insists on using the existing copy of Ubuntu in the Ultrabay slot. Goes fine. Run Update to bring system up to date and then shut machine down and reinsert second hard drive in the Ultrabay. Boot machine up and Ubuntu registers second drive fine with the other Ubuntu installation and backed up data on it. I kick myself now of course. I should have used the Copy command but anyway . . gksudo nautilus to give me root on the file manager. Navigate to Home on the second drive, click on 'My Document' folder and click on 'Move to Desktop'. I assumed that it would move the folder to the Desktop on the just installed machine and I could organise the files from there. All seemed to go well. File transfer ran at 24, 25mb a second. Soon through even though it was 8.1 gig of data. Switched to Desktop and nothing there. With that horrible sinking feeling, I search both machines but to no avail. The My Documents directory no longer exists, anywhere. Pretty despaerate here. The data is my daughters complete with university work, photos, the lot. Been telling her now great Linux is . . Should have used 'Copy' . .

---

### Post by ibjsb4 on 2013-02-13
I just tried this and found out that the folder moved to desktop will not appear in nautilus user account.  But if I gksudo nautilus and go to desktop, its there.  I do not know why this happens, but have you tried this?

---

### Post by simonbing on 2013-02-13
Whey . . !!! It's there! Never thought of that! Many thanks. Saved my reputation as well as Ubuntu's on that one. ;)

But . . I've now sorted the files into the proper folders and changed the permissions so my daughter has full access. I've checked them and deleted them from the old 'My Documents' folder as I copied them over. The problem is now that the rubbish bin won't allow me to empty it, permanently delete the old files. This is even if I'm working as root through gksudo nautilus. The file manager won't even show the files in the window even though I know there's 8 gig of files there. 

The error message is: The folder contents could not be displayed.  Sorry, could not display all the contents of "trash": Operation not supported.

I really need to delete them as its only a 40 gig hard disk. Any ideas?

---

### Post by ibjsb4 on 2013-02-13
Empty your trash in terminal.  The first link should do the trick, but there are other ways to do it in terminal if that first link will no work.

And glad you found your folder :)

[http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=empty+trash+in+terminal&sa=Search&cof=FORID:9](http://www.googlubuntu.com/results/?cx=006238239194895611142:u-ocqbntw_o&q=empty+trash+in+terminal&sa=Search&cof=FORID:9)

---

### Post by simonbing on 2013-02-13
This is getting a bit beyond! None of the terminal commands work. I have been able to find my way, signed on as root, to the actual trash directory and try deleting them 'direct'. No go. Tried changing permissions. Still no go. The folders I'm trying to delete all keep coming back with an extra .2 after them. Have tried moving them back to the Desktop and succeeded but even deleting them one by one doesn't work. They just line up back in the folder again. Tried deleting the files in the directories and thought that was working until I discovered they were just being 'reborn' in the main files folder. I'm beginning to think the easy way to deal with this is to cut my losses, backup the data again and re-install. The things just don't want to die! I can just imagine having nightmares on this!! :D

---

### Post by simonbing on 2013-02-13
Solved it although unhappy with the way I had to do it. Signed on as root. Opened Nautilus, 2 panels, Ctrl H, went to root's trash and moved the files to my daughter's trash. Did the same with all the files on the root desktop. Closed nautilus, exited root, emptied the trash from my daughter's desktop. No problem. I'm going to keep an eye on it cos I don't think it should be the case that the root trash bin has no Delete from Trash option on right click. I'll take a look at my setup too I think but it seems a bit dodgy . . Something not quite right somewhere. 

PS. Many thanks for the help.

---

### Post by ibjsb4 on 2013-02-13
Thats one heck of a fix :) but congrads, you solved it.

There is an option in nautilus to bypass trash and just delete.

In nautilus:  Edit>preferences>behavior>delete/bypass trash

Your finding things a little slow?  Give Ubuntu 2D a try.  Its and option you can choose at boot (login).

---

