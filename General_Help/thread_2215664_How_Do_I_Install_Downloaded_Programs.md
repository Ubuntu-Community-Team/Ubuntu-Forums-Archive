---
title: "How Do I Install Downloaded Programs?"
date: 2014-04-07
forum: General Help
---

### Post by Smallwheels on 2014-04-07
I did a search for this but there were so many post titles with How To.... that I couldn't find what I needed.

I want to load the latest version of LibreOffice. 

I have had problems with an older version of LibreOffice (3.5.7.2) and I want to run the newer version. The latest stable one is 4.2.2. 
It has been downloaded from the LibreOffice site into my computer. I have opened or extracted the files. The first one is LibreOffice_4.2.2.1_Linux_x86-64_deb. Inside that are a couple of folders. One is DEBS and the other is readmes. 

What are the steps I need to do using the terminal to load LibreOffice on my machine? These instructions probably will be the same for all programs with just a name change. Once I learn how to do this it should work for any program I download.

I hope this is an easy one that gets a quick reply. I want to start working with this again today. 

Thank you for your help.

---

### Post by mcduck on 2014-04-07
In general, downloading software manually is the last thing you want to do. For example in this case a quick google search reveals that Ubuntu's LibreOffice packaging team maintains a PPA repository with up-to-date versions: [https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/~libreoffice/+archive/ppa")

So, the best thing to do is ignore the files you have downloaded, and instead just add that repository to your software sources and you'll get the latest version as a normal update (and will continue to get the updates as well):
```

sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade

```

(and in cases you really can't find a repository with software you need, you don't need to extract .deb packaes, simply double clicking them should open them in the Ubuntu Software Center and allow you to install the package. Or you can install from terminal by running "*sudo dpkg -i /path/to/thepackage.deb*". Of course you'll loose the benefit of automatic updates you'd get from using a repository)

---

### Post by Smallwheels on 2014-04-07
Thank you mcduck for giving me that advice. It makes sense. Even with that good information I still want to learn how to do this. I see you have entered this: "*sudo dpkg -i /path/to/thepackage.deb*". Could you give an example of what would go into each of these sections you have here? Specifically tell me how to fill in path, to, the package.deb.

This file is in an external drive buried in a few layers of folders. Is that the path? How do I properly input that into the command? This is interesting. I'm glad to have somebody teach me how to do this.

---

### Post by hardkhora on 2014-04-07
SmallWheels, it would be easier to follow the first steps taht McDuck mentioned: > [COLOR=#000000] simply double clicking them should open them in the Ubuntu Software Center and allow you to install the package.[/COLOR] before using the command line. What happens when you double click the LibreOffice_4.2.2.1_Linux_x86-64.deb file? If it isn't asking you if you want to install (should prompt you for you password as well) then what is happening after you double click it? Hope this helps.

---

### Post by ajgreeny on 2014-04-07
Let's assume you have downloaded a package.deb file to your external disk folder.  You can now use one of two ways to install that deb file with the dpkg command.
[LIST=1]
[*]You either change directory to the folder in terminal using command ```
cd /media/diskmountpoint/foldername/folder
```, then run command ```
sudo dpkg -i package.deb
``` or
[*]You can just use one command which does both the previous actions in one by using the full pathway to the deb file, ie ```
sudo dpkg -i /media/diskmountpoint/foldername/folder/package.deb
```
[/LIST]

It is impossible to know what your external disk mountpoint will be called but you can find that from nautilus or your alternative file manager simply by looking in /media, but it will most likely be **/media/username/diskmountpoint/foldername/folder**.  To save manual typing use tab completion of names, ie start typing the first letter or two of the foldername you have seen in nautilus then press Tab; as if by magic the name will autocomplete, and you can keep repearting that until you get to the package name itself.

---

### Post by mcduck on 2014-04-07
the easy trick is to just drag & drop the .deb file to the terminal, at least gnome-terminal will automatically fill in the full path and file name for you.

But if you want to do it manually, you'll just need to type in the full path of folders, starting from the root of the filesystem ("/") all the way to the folder where your file is, and then the name of the file itself. It's nothing complicated, but you'll need to be at least a bit familiar of the filesystem hierarchy Linux uses. Like  ajgreeny said, usign the Tab key to autocomplete parts of the path can help, and you can always use the basic commands like "cd" and "ls" to move around the directories and to check where you are. I'm sure there's some web page with much better tutorial on traversing through directories and finding things in Linux than what I could ever write here so I'm not going to even try to go into further details. I'd say the best way to learn is to give it a try, in the worst case you'll just get an error about not being able to find the file...

---

### Post by Smallwheels on 2014-04-07
Good information. I went to the file system icon and clicked it. Inside it I see a folder named media. When I click it it takes me to my external hard drive folder icon named TOSHIBA EXT. Inside that the folder hierarchy just leads me to the file. Do I need to enter each folder name with a slash all the way down to  the ultimate file?

---

### Post by mcduck on 2014-04-07
> **Smallwheels said:**
> Good information. I went to the file system icon and clicked it. Inside it I see a folder named media. When I click it it takes me to my external hard drive folder icon named TOSHIBA EXT. Inside that the folder hierarchy just leads me to the file. Do I need to enter each folder name with a slash all the way down to  the ultimate file?

yep, that's how it works.

Although you'll have to deal with the space in the name of your hard drive's name (otherwise the shell won't understand that the path continues after the space in the command). You can either escape the space with a backslash, or put the whole path in quotes:
```

sudo dpkg -i /media/TOSHIBA\ EXT/LibreOffice_4.2.2.1_Linux_x86-64.deb
```
or:
```
sudo dpkg -i "/media/TOSHIBA EXT/LibreOffice_4.2.2.1_Linux_x86-64.deb"
```

Or you can just cd all the way until you are in the same directory with the .deb file, and then simply run "sudo dpkg -i thepackage.deb" if you prefer.

---

### Post by grumblebum2 on 2014-04-07
Another way to get the correct path to a file is to navigate to the file in the browser
and right click on it and copy.
Then in gnome-terminal you can right click and choose "Paste Filenames".
In text applications you can just use "Paste".

---

### Post by 23dornot23d on 2014-04-07
or if in dolphin navigate to the file then press f4 

and a terminal will open up below the file manager (kde not sure if its the same in all desktop environments) but should be .......

---

### Post by Smallwheels on 2014-04-07
OK I tried this two ways. Somehow I'm making a mistake because when I hit enter after entering the information all I get is this symbol; >. The prompt stays white instead of blinking. If I move the cursor around or hit enter again it will blink a bit but otherwise will stop.

These are the two ways I typed this:
```
sudo dpkg -i "/media/TOSHIBA EXT/Ubuntu files/Documents/Computer Programs/LibreOffice_4.2.2_Linux_x86-64_deb.tar.gz/LibreOffice_4.2.2.1_Linux_x86-64_deb"
```

```
sudo dpkg -i /media/TOSHIBA\ EXT/Ubuntu\ files/Documents/Computer\ Programs/LibreOffice_4.2.2_Linux_x86-64_deb.tar.gz/LibreOffice_4.2.2.1_Linux_x86-64_deb
```

You can see that in the first one I used quotation marks so that I could just copy the path the way the file names appear in each folder. Then I tried using the backwards slash to signify a space. I did not use quotations marks with that one. 

You might have noticed that the first instance of me typing the LibreOffice version doesn't have the 1 as part of the name. The folder name doesn't include it. The file inside that folder does have the 1 behind 4.2.2. I thought I should mention that in case you thought I was leaving that out. 

Am I not starting early enough in the path? I must be missing something or typing something incorrectly. I'm eager to get this right.

---

### Post by 23dornot23d on 2014-04-07
you have _deb at the end ........ usually it is .deb

at the end .........

**sudo apt-get update**
[B]sudo apt-get install dolphin

dolphin[/B]

navigate using the file system folders to the area where the file is ( Function key f4 on the top )

**press f4**

Then type in the command you want to use in that directory .........

( [COLOR=#ff0000]**sudo gdebi filename.deb**[/COLOR] ) is another way to install things .........

---

### Post by Smallwheels on 2014-04-07
> **23dornot23d said:**
> you have _deb at the end ........ usually it is .deb

at the end .........That is interesting. I have not modified the names of any of these folders. Maybe I need to go add another folder to the path. Inside that last folder is another one named DEBS. I didn't think of that until I investigated the names of these folders. Inside the DEBS folder are a lot of files. There are no more folders inside.

---

### Post by 23dornot23d on 2014-04-07
can you give us a screen shot of what you see ....... in that last folder ........

use dolphin ( its a file manager and you point and click till you get into the folder you want - then just press f4 the function key at the top of the keyboard )

its easier than having to type all that command in ...... and its better to learn efficient ways early on .

there is also a article here on all the methods for installing things ..... the hardest tend to be later on in this document/thread.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Hope you do get it installed though .....

> 
**Using GDebi to install packages**

 GDebi is a simple tool to install *.deb*  files. It has a graphical user interface but can also be used in your  terminal. It lets you install local deb packages resolving and  installing its dependencies.. It automatically checks packages for their  dependencies and will try to download them from the Ubuntu software  repositories if possible. You may first need to install GDebi - simply  install the gdebi package using one of the package managers listed above, or open a Terminal and type sudo apt-get install gdebi. 
Once  you have installed GDebi, use the File Browser to find the package you  wish to install. Package files will look similar to this: 
[IMG]https://help.ubuntu.com/community/InstallingSoftware?action=AttachFile&do=get&target=deb_package.png[/IMG] 
Double-click  the package to open it with GDebi. If all dependencies have been met  for the selected package, simply click the 'Install package' button to  install it. GDebi will warn you if there are unmet dependencies, which  means that there's dependencies that aren't resolved in the repositories  that you're using. 


I see it now - its archived - so the first step is to get it out of the archive ...... big file too 210 meg

[IMG]http://i.minus.com/ibguQbsboMQaUR.png[/IMG]

---

### Post by grumblebum2 on 2014-04-07
Look at the wiki ....[https://wiki.documentfoundation.org/Installing_LibreOffice_on_Linux#Terminal_Based_Install](https://wiki.documentfoundation.org/Installing_LibreOffice_on_Linux#Terminal_Based_Install)

I don't think the package you install is just a single deb file.
There are easier ways to install but if you just want to learn read the wiki.

---

### Post by Smallwheels on 2014-04-07
I typed in the same thing and added the last folder DEBS and got this:

 cannot access archive: No such file or directory
Errors were encountered while processing:
 /media/TOSHIBA EXT/Ubuntu files/Documents/Computer Programs/LibreOffice_4.2.2_Linux_x86-64_deb.tar.gz/LibreOffice_4.2.2.1_Linux_x86-64_deb/DEBS

b a s h :  /media/TOSHIBA EXT/Ubuntu files/Documents/Computer Programs/LibreOffice_4.2.2_Linux_x86-64_deb.tar.gz/LibreOffice_4.2.2.1_Linux_x86-64_deb/DEBS: No such file or directory

Those attempts were using the quotations marks around the whole thing.

This is what I got when using the backslash before spaces:

dpkg: error processing /media/TOSHIBA EXT/Ubuntu files/Documents/Computer Programs/LibreOffice_4.2.2_Linux_x86-64_deb.tar.gz/LibreOffice_4.2.2.1_LibreOffice_x86-64_deb/DEBS (-- i n s  t all):
 cannot access archive: Not a directory
Errors were encountered while processing:
 /media/TOSHIBA EXT/Ubuntu files/Documents/Computer Programs/LibreOffice_4.2.2_Linux_x86-64_deb.tar.gz/LibreOffice_4.2.2.1_LibreOffice_x86-64_deb/DEBS

I broke up the words b a s h and - - in stall in case they were commands.

---

### Post by 23dornot23d on 2014-04-07
There is a step to get them unarchived 

[IMG]http://i.minus.com/iwB6xi0k52leO.png[/IMG]

Which when unarchived will look like this screenshot below ......... ( press f4 to get the terminal below it )

This will make the step of installing them all much simpler than the way you was trying to do it ........

[IMG]http://i.minus.com/iNJMyYixoDrUx.png[/IMG]


ok I re-read your first post again ........ you have extracted them 




  you can do it with dpkg using a * which will do them all at once ......... once in that directory.
the one you downloaded and unpacked them to .........

[SIZE=5]sudo dpkg -i *.deb[/SIZE]

Think that will suffice .......

[IMG]http://i.minus.com/ibsawm3yDKI23l.png[/IMG]

yep that works ok ....... its run on my system and its all installed ok


[IMG]http://i.minus.com/ig8dPtj32l0g8.png[/IMG]

---

### Post by Smallwheels on 2014-04-08
I don't have the dolphin file manager. At this time I do not want to change file managers. Your idea of seeing images might be helpful to you and others to help me solve this.
I do have the files extracted. I have decided to show my file windows.

The first one shows the file path on the top of the screen with the tar.gz file. 
When I click that one, you see the LibreOffice folder. The archive was unpacked before this second folder opened in a new window. I put it on top of and below the first window. This is still within the first image.
In the second image I click to open that file and you see the DEBS folder and the readme file.
In the third image when I click the DEBS file you see the contents of that one. 

These should show exactly what I have on my machine. I just need the correct command to get this moving.

---

### Post by su:bhatta on 2014-04-08
Did you read the 'Readmes' that is there in your second screenshot. 
It should give you details on how to install LibreOffice.

By the looks of it, LibreOffice download gives all libraries that are dependencies too. 
You have to install all those .Deb files in your third screenshot and you will have a new installation of LibreOffice.

Just navigate to the directory where you extracted the .Deb files and Run 
> sudo dpkg -i *.deb

as pointed out by 23dornot23d.

That should work.

---

### Post by grumblebum2 on 2014-04-08
> **Smallwheels said:**
> I don't have the dolphin file manager. At this time I do not want to change file managers. Your idea of seeing images might be helpful to you and others to help me solve this.
I do have the files extracted. I have decided to show my file windows.

The first one shows the file path on the top of the screen with the tar.gz file. 
When I click that one, you see the LibreOffice folder. The archive was unpacked before this second folder opened in a new window. I put it on top of and below the first window. This is still within the first image.
In the second image I click to open that file and you see the DEBS folder and the readme file.
In the third image when I click the DEBS file you see the contents of that one. 

These should show exactly what I have on my machine. I just need the correct command to get this moving.

May be wrong but from your pics it appears you haven't actually extracted the files...you're just viewing them in the archive manager.
Right click on the download and > Extract Here.

The libre office download is unusual in that it's an archive of numerous debs.

---

### Post by 23dornot23d on 2014-04-08
As stated ( on the last page/post ) - the files have not been extracted yet .......... see my post # 14 

I used the first method which automatically open the file up into the extraction program.

The second option was used in                                                                                      [**[COLOR=#000000]Smallwheels[/COLOR]**]("http://ubuntuforums.org/member.php?u=1048082")      
                         [IMG]http://ubuntuforums.org/images/ubuntu-VB4/statusicon/user-offline.png[/IMG] users case ...........

and the file is sitting in place as a compressed file ( just like downloading a zip file for windows ) its compressed
still as shown in this picture ( so the next step is to get it out of that container and uncompress it ..........

[IMG]http://i.minus.com/iwRIzcDhUwYBu.png[/IMG]

What we need to do now is to select the LibreOffice_4.2.2.1_Linux_x86-64_deb folder in the screenshot above ..... under Name.

 and then pick on the icon that comes up with the word Extract 

( Extract may only show - as you move your mouse over the icons above the file that look like pulling things out of a box )
( * or even right clicking on the folder in the extract window will bring up options - a standard in windows too - to right click the mouse button
    on a file gives more options )

___________________________________

Then although in my screenshot it is not exactly the same as above - it does show what the result will be ..... the file
will move out of the archive ( compressed container ) and into a place where we can use it to install the files to the
hard drive.

[IMG]http://i.minus.com/iKZ0PkKg49ALQ.png[/IMG]

It should be then a case of following the instructions for installation and extraction - from post # 17 ...........

If any problems should arise - please post back - the screen shots help to show some of the problems too - thanks for posting
them - as it shows the extract button is not obvious .......... but that is what we do with .tar.gz

( Same as a windows user would do with a .zip file - this explanation is for anyone that may be coming here from XP / Windows )

---

### Post by ajgreeny on 2014-04-08
If I remember correctly, the only way that it is possible to install the .debs extracted from the archive is using the **sudo dpkg -i *.deb** command after navigating to the /DEBS folder where all the deb files are, as each deb is dependent on at least one or more of the others.  It is therefore impossible to simply double-click on one of them to install it; you will get a "dependency not found" error.

My file browser (thunar from Xubuntu) also has an "Extract here" entry in the right click context menu, and I think nautilus does also, so you don't need to do anything except right click on the tar.gz archive, and then click on "Extract here" to get the /DEBS folder.  Now change directory to the /DEBS folder and run the **sudo dpkg -i *.deb **command to install them all.

We do, however, seem to be going round in circles here, and even at this late stage I would suggest you go back to the post #2 from mcduck and think about doing this the easy way using the ppa.  Not only will this install LO 4.2.3.3 now, but will also keep it updated as newer versions are released.

---

### Post by Smallwheels on 2014-04-08
Now there is conflicting information here. A couple of you say I need to use:```
**sudo dpkg -i *.deb** 
``` This might be right because the other way didn't exactly have an effect. Of course we have learned that the folder's contents weren't extracted already so that might have been the reason. 

I understand the advice to do it the easy way by using the Software Center or PPA route. I did read the readmes file. It contains good information I'm sure but the terminology is beyond my understanding at this time. That is why I requested help doing it this way. This will also teach me the reasons why things are done this way. Already I've learned that there is a need to extract files. I've learned that a backwards slash tells the terminal that there will be a space behind a word. I've learned that a path contains the names of all of the folders on the way to the final file to be opened. I've learned that there is a way to combine commands in one longer line of instructions. 

I went to the original zipped file and clicked it. The machine opened it. 
Then I saw the LibreOffice file with a blue folder. I clicked to open it and that is when the DEBS and readmes files were shown. 
I right clicked the DEBS folder and saw the Extract menu choice. I clicked the Extract choice and got a new window with the same file names as the last image I took yesterday. The difference is that these are arranged in icon view instead of list view. Are these files now extracted or must I extract them again? 
I took a screen shot of the DEBS when it opened after I selected Extract. If I highlight all of the files I can also select Extract. It almost seems like the Extract menu choice also means open anything.

---

### Post by grumblebum2 on 2014-04-08
In the the file browser right click on your Debs folder and select copy or get the address from the addressbar by hitting ctrl+l (lower case L). 
In the terminal enter **cd** followed by a space then right click and "paste filenames" or just "Paste" if you copied from the addressbar. Press enter.
Now type **ls** in the terminal and press enter. (That's a lower case L again)
If you see a whole lot of debs your in the right directory.

Now run...
```
sudo dpkg -i *.deb
```

**cd** ....change directory
**ls** .....list directory contents
**Tip:** Install **nautilus-open-terminal**. This will provide a right-click "Open in Terminal" option in any Nautilus window.

---

### Post by 23dornot23d on 2014-04-08
or even try the command you started with earlier ...... its here ......... this time with *.deb

```


**sudo dpkg -i /media/TOSHIBA\ EXT/Ubuntu\ files/Documents/Computer\ Programs/DEBS/*.deb**


```

I think that should do it ........

 ( one line of text above - it just needs cutting and pasting into a terminal - then press return - thats it job done )

____________________________________________________________

( this is so anyone looking can check - from that last screenshot the user posted )

[IMG]http://i.minus.com/ipXdMns48PwP3.png[/IMG]

---

### Post by Smallwheels on 2014-04-08
grumblebum2 I tried to do as you instructed. It seems that the DEBS  window that I opened doesn't have an address bar. What I did was right  click on the open space within the folder and select properties. In that  window there was an address. I copied it. Then I entered the cd, a space, and pasted the address. When I hit enter it said no such file or directory. 

Thank you for defining cd and ls.

During this attempt the message from 23dornot23d came in. I saw the code and wondered why DEBS was at that point instead of the two names of LibreOffice that were previously in the path to the DEBS folder. Is this because the Extract command placed that folder in the same folder as Computer Programs? 

I copied and pasted the code into the terminal and it did start loading file after file and then unpackaged and put everything into the machine. I now have the entire Libre Office suite. 

What does the * symbol mean? 

Thank you all for your assistance. I will have a couple more questions about these commands in a little bit. First I must enter some data into a LibreOffice file that I have had to put off for a couple of days.

---

### Post by 23dornot23d on 2014-04-08
> 
During this attempt the message from 23dornot23d cam in. I saw the code  and wondered why DEBS was at that point instead of the two names of  LibreOffice that were previously in the path to the DEBS folder. Is this  because the Extract command placed that folder in the same folder as  Computer Programs? 



Yes to this - your original command included the tar.gz .......... because you were trying to run it from the archive folder .

This was where I first joined this thread - as I could see that was not going to work out ........ the main thing that caught my attention was that
there was not a .deb at the end ....... and that is now a different situation ......... we only have that last line of text to run and all the files
should install nicely and you will then have the latest version of LibreOffice up and running ..........

> 
I copied and pasted the code into the terminal and it did start loading  file after file and then unpackaged and put everything into the machine.  I now have the entire Libre Office suite. 


Yep that is the one thing you see - all the files install into place - this is what I did too last night and then the LibreOffice on mine came up
in cairo-dock to run ( seems like a new feature - any new program installed is automatically shown and it asks do you want to run it )

But I do not know if you know what cairo dock is .... but it is similar to having Unity with symbols/icons to choose for your favourite programs.
 [http://glx-dock.org/](http://glx-dock.org/)

Can be a nice addition for some desktops ......... 
( but if you run Unity - then Unity acts the same as a dock ........ but it will not move and that is why sometimes its nice to be able to configure things the way we like them )

What suits me - may not suit everyone - but this is how I lay my desktop out with cairo-dock at the top ....... and favourite programs ready to use in it.

[IMG]http://i.minus.com/ivmwLZ5vQQ6Vm.png[/IMG]
_______________________________________________________


The * symbol means to install everything ...........

its what we would use say we wanted to see all the files that were pictures in a directory ..... like 

ls *.jpg

This command would list all the [SIZE=4].jpg[/SIZE] files .......... in a directory .......

What we are doing is ensuring we install every file you downloaded - as some depend on others to be there for a proper installation
to take place .........

Will see if I can find the man page for it ( they are usually called wildcards ) [http://www.linfo.org/wildcard.html](http://www.linfo.org/wildcard.html)

---

### Post by Smallwheels on 2014-04-09
Thanks for the answer 23dornot23d. I opened the latest version of LibreOffice and it has a different layout. I typed in some of my past information that had been entered into a text editor and then added some more information. LibreOffice has an automatic save function. When it came on it showed a progress bar across the bottom. As it progressed it froze. Yep. The stupid program is malfunctioning. So I had to force quit it. I entered the information again and then went to save the file. The same thing happened when using the save button. Now I'm off to the LibreOffice.org forum to ask why this is happening and how to fix it. 

I did try Abiword once. Several people have commented that it is a good word processor. It didn't function well. It was buggy. Does anybody have any suggestions for something else besides OpenOffice? I couldn't get that to load on my machine and it requires Java which I don't even know if I have installed.

---

### Post by 23dornot23d on 2014-04-09
What version of Ubuntu are you using - type these commands in will show the version and the kernel in use.

[B]lsb_release -a

uname -a

Do you want me to try anything on the version I have installed to check these problems out you are getting
maybe your system needs updating ........ or is it uptodate ?

( also look in your document - Tools - Options - Save - General )

You can change the autosave and try just saving manually - if that is what caused yours to freeze up ..........

Mine appears to be working ok - but then I am in the latest version of Ubuntu ....... which comes out for main use on
the 17th of this month ..... maybe it will be something you consider then .........

The only other program I can think of for word processing ........... scribus ......... [http://www.scribus.net/canvas/Scribus](http://www.scribus.net/canvas/Scribus)
[/B]

---

### Post by Smallwheels on 2014-04-09
Thank you for offering to help in this way. I think it is too early to go through all of that. Scribus looks wonderful but it is a little different from just creating documents. All I need is to create text documents and sometimes to add images to them. 

One thing you could do is give me the correct commands to uninstall all of the LibreOffice suite and all of its dependencies. If the ask.libreoffice.org forum can't assist me with this then I will uninstall the new version and go back to the older version that functioned OK but was buggy regarding saving to my external drive. 

When 14.04 LTS arrives I will just switch to that using a fresh installation. I have learned how to use GPartEd and Unetbootin to put .iso files on a USB stick. I have done it several times with success. Unfortunately I haven't found a perfect OS. If I knew how to tweak them like an experienced person can, I probably could make one suit me. I liked OS X but grew to dislike the way Apple does business. I tried Trisquel, a totally Free OS, but it didn't function well and I really need Flash and the restricted extras package. I didn't like Open SUSE 13.1 because it took too many steps to load things. Bodhi seemed promising but it was super buggy on my HP. I couldn't get any help with my specific problems on their forum. Elementary is one I really liked in addition to Ubuntu. Some people dislike Unity. I liked it but didn't like that it was so slow on my low powered machine. It has a 2009 AMD 2.3 GHz Sempron LE 1300 with 2 GB RAM. My next computer is going to be a Chrombox or Chromebook.

---

### Post by 23dornot23d on 2014-04-09
The command to remove them is
sudo dpkg -r package_name

So possibly - but check with the others that have removed them before - it should be just this ........
but seeing I have never had to use it before - then its best to check with those that have ........

> 
**sudo dpkg -r /media/TOSHIBA\ EXT/Ubuntu\ files/Documents/Computer\ Programs/DEBS/*.deb**

But I would check with others on here that use this on a regular basis ....... as there is another
command to purge the configuration files too .

You need to know which is a safe way and I do not usually have to remove any packages using dpkg ........

All I did was show you how to use the command you were are having problems with.

---

### Post by mcduck on 2014-04-09
Instead of removing, I'd recommend doing what I actually suggested as being the best option in the second reply to this thread, and add the PPA repository for LibreOffice. That repository has the very latest packages (one version beyond what you just downloaded) and simply adding the PPA and running normal updates will replace the version you now have with the one from the PPA.

Even better, the packaging team actually packages the software for Ubuntu, which makes them better optimized than the upstream packages from the web site.

And in the end even if they don't work, using them allows you to get support directly from the packaging team, and you can also use ppa-purge to get back to the versions in Ubuntu's official repositories without having to uninstall LibreOffice to do that.

So, the first command adds tha PPA and it's GPG signing key, the second command updates information about available packages in all your software sources, and the last one installs all available updates:
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by monkeybrain20122 on 2014-04-09
+1 to ppa. 

But just for general info, you can remove by 
```
sudo apt-get remove --purge libreoffice*
```

It doesn't matter how you installed the .debs,--with dpkg -i or from the repository,-- as long as they are .debs the package manager and apt-get handle them the same way once they are installed, that's why upgrading with the ppa automatically removes your manual installed version. (**Edited**: this will not work, for example, if you install from source with "sudo make install" since in this case no .deb is created)

Also, right clicking a .deb may have two possible consequences depending on your DE and how you set your defaults. In Ubuntu the default behaviour is that the Ubuntu Software Centre will open and try to install the .deb. But since it is slow I prefer to use gdebi, so I installed it and made it the default application to install .debs by right clicking. In KDE muon may open to try to install the .deb.
 
However, a .deb is also an archive so File roller (or its equivalent in other DEs) may also open the .deb file, but instead of installing it it will open it as an archive (that seemed to be what caused the confusion a few pages back)  In that case you need to reset the default application for .debs (usually by right clicking and go to Properties, some variations depending on DEs and file manager) Sometime you may want to open a .deb as an archive: a case in point, in order to install 64-bit google-earth you need to first open the deb to edit a file and then rebuild the .deb because of a google packaging bug.

Finally in the case of LO the tarball extracts to not one, but a large number of debs where some are dependent on the others being installed, so right clicking each would not work,--not to mention very inefficient even if they are not inter-dependent. So you use the command line 
```
cd /path/to/folder/that/contains/all/the/debs
sudo dpkg -i *.deb

```
 cd means change directory, so now you're in the folder where the .debs are.
* is a wildcard meaning 'anything'.  so basically you tell dpkg to install everything, leaving it to sort out the interdependencies.

---

### Post by hardkhora on 2014-04-09
> **mcduck said:**
> the first command adds the PPA and it's GPG signing key, the second command updates information about available packages in all your software sources, and the last one installs all available updates:
```
sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get upgrade
```
I'd recommend following mcduck's advice on post #2 and post #32 and let everyone know what happens after that.

---

### Post by Smallwheels on 2014-04-10
This was a great learning experience. As of now the ask.libreoffice.org site hasn't given me an answer. I have found that the LibreOffice Impress software is functioning fine in the limited testing I did. It does allow me to save presentations. So the bug is related to Writer. I don't use spreadsheets very often so I don't know when I'll get around to testing that one. 

To get some work done I tried using Google Drive. I don't believe it is the ultimate solution but it will do for now. It's only a few days until 14.04 arrives. I can cope with my situation until then.

---

### Post by grumblebum2 on 2014-04-10
Smallwheels keep on learnin'
Rollin, rollin........
:P

---

### Post by 23dornot23d on 2014-04-10
Mine was fine - then yesterday I used the commands to add the PPA and upgrade to that latest version -  now 2 errors pop up before
going into documents - to do with authentication ....... 
( I have a feeling this is caused by the untitled document not having access from the user ) might also explain why it hangs-if the user
is trying to write into any area they do not have write access to .... worth checking out I guess ........... as mine cleared as soon
as I created a new untitled.doc .........

 ( So the PPA method might still have given slight problems .... ) this is just as an update to this thread ...... 

But I agree - upgrading apps rather than removing them - in my mind is always a better thing to do with Linux ........ 
especially when dpkg allows lots of files into the system - but then takes some very careful removal as lots of
shared libraries could get messed up here .........

We wait and see if in the future there ever comes a possible way of packaging things ever comes up where users can download a package into
a folder and use it from there with all the dependencies in that folder  ..... 

Otherwise I think its better to stick towards the top of this (Installing Software) list when installing larger packages - when possible to do so.
[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

Different ways of doing things ....... but getting more risky as you go down the list ........ but if the user has the right
knowledge - which sometimes comes with trying things and failing ..... then it becomes more apparent why its advised
to use the package managers ........ 

( Glad things did not mess up too much - and its the last time I use dpkg as a means of giving normal users installation instructions .... even
if I see that is the way they want to go in the future - its not a good way - because reversing the actions seems to be very difficult to do safely )

I am usually against using PPA's too as these when you search on them can start causing problems ....... they are developers own repos and
the methods they all use to keep them uptodate and tested is a way where mixing and matching starts to occur 
_______________________

Safest ways I know

USC
Synaptic Package Manager
Muon

_____________________________

Recommended ways I know

Apt-get install
Aptitude install


__________________________

Still package controlled - ways I know .......

Gdebi
Alien for rpms .... ( if ever redhat package manager installs are needed - very rare nowadays )

___________________________

Package controlled - but all sorts of things working and partially tested can be added this way ..... but easier to remove than the ones following this

PPA's ( using other repositories - which can cause problems - when coming to upgrading systems if still active )

_______________________________________

Base of all installs - and developers and experienced people may be able to use these safely with the right knowledge

dpkg ( which in 10 years of using Linux - this was the first case of doing it this way only because that was also mentioned in post #2 )

_______________________________________

Definately only for Developers and tinkerers that do not mind breaking their own systems irreparably .... such a re-install may be needed 

But if it is the very last thing possible to do then anyone reading this may benefit from checking this thread below out by compiling into
another area /opt .

>>>>>>>>>>>>>>>>>>>> [http://ubuntuforums.org/showthread.php?t=778330](http://ubuntuforums.org/showthread.php?t=778330)  <<<<<<<<<<<<<<<<<<<<<<<<<

but ....

Compiling and inserting source code manually directly into the system is ( probably the most dangerous - as you can totally wreck a system this way )

___________________________________________________

To finish .........

Good to hear the user has found a workaround for the time being - until the system changes to the 14.04 .......
which is not too long away now - 17th April ....... 

( but it is often a good idea to wait for a while to let any unseen problems get fixed in the first few weeks after launch - IMHO )

and often better to install alongside their own systems first to check everything works ...... 

( as there are no simple ways of going back or doing a restore ) unless they have clear means of creating a backup before they do anything.

One day there will be a backup system - that simply takes a snapshot before doing upgrades.

Until that day ...... it is probably safer with doing a clean install alongside the users own System in its own partition.
( and keeping all user data on other separate partitions )  

( But people will probably debate this - need clear methods for getting the best system without destroying a working one and options to go back should they. )

If anyone should have any better methods - please put them forward ....... ( as I too am always willing to learn )

---

