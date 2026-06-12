---
title: "[SOLVED] Making Windows Internet Explorer shortcuts (.url) work in Ubuntu"
date: 2007-07-07
forum: General Help
---

### Post by oomingmak on 2007-07-07
I have a massive amount of .url internet shortcut files (from Windows) that I'd like to use in Ubuntu.

The .url files are basically plain text files with the web site address stated as a value (URL=http://websiteaddress.com) under an ini style section heading [InternetShortcut].

How would I go about creating a 'file type' for .url files so that when clicked in Nautilus, it would read the URL value contained in the file, and then pass it to Firefox. I'd like to just click the .url file and have it launch Firefox and go the site stated in the text file (just as it does in Windows). This would save me from having to maintain two separate lists of shortcuts or bookmarks.

At the moment I am having to open each shortcut in a text editor and manually copy the web address and then paste it into Firefox's location bar (which gets tiresome very quickly).

Maybe this has been done already, but none of my searches have turned up anything.

Thanks.

---

### Post by strider1551 on 2007-07-07
I've never heard of or used .url files.  Considering their apparent obscurity, I doubt there's anything out there.

There is a solution, though.  [This page]("http://www.gnome.org/learn/users-guide/latest/gosnautilus-440.html") describes how to run scripts from nautilus.  You need to make a script (whether it be in BASH, python, perl, or whatever) to find the url in the text file and open firefox to that url.

The script should be fairly straight forward:
1. read the file
2. use a regular expression to grab the url
3. execute "firefox address"

Once you have the script, you should be able to right click on the .url file and select the script in the menu.

---

### Post by oomingmak on 2007-07-07
Thanks for your reply. :)

> **strider1551 said:**
> I've never heard of or used .url files.  Considering their apparent obscurity, I doubt there's anything out there.

They are hardly obscure. The entire Internet Explorer bookmark system is based on it.  Whenever anyone using Internet Explorer makes a shortcut, they are making a .url file (it's just that the extension is permanently hidden, so they probably don't know the file type).



> **strider1551 said:**
> You need to make a script (whether it be in BASH, python, perl, or whatever) to find the url in the text file and open firefox to that url.
I'll take a look and give it a go, but I've never written a script before and I don't have a clue how to use regular expressions.



> **strider1551 said:**
> Once you have the script, you should be able to right click on the .url file and select the script in the menu.
Is that how I would launch it?

I would rather 'associate' (don't know the Linux term) the file, so that it launches when clicked, rather than having to right-click and select a sub-menu every time.

---

### Post by oomingmak on 2007-07-07
OK, I've done a little more digging and there may be another way to go about this.

I have dragged web urls from Firefox to the Ubuntu desktop and it creates a shortcut file (with a Globe icon) that has no file extension. This is very similar to IE shortcuts.

I opened one of these files in Gedit and found that it is a .desktop file (but the extension is hidden just like .url is hidden on Windows. 

The format of the content is almost identical to a .url file. You have an ini style section heading: [Desktop Entry]  and then the web site url is in a value called URL    URL=http://ubuntuforums.org/    This is exactly the same as Windows.

The only differences are that Windows uses [InternetShortcut] as the section heading rather than [Desktop Entry] and in the .desktop file there are a couple of extra entries for Version number and Encoding.

Given the similarity of the files (and the fact that .desktop files already work in the manner that I'm trying to get .url files to work in) I would have thought that Nautilus already has everything that it needs to read the URL. It just needs to be told to read .url files in the same way as .desktop files.

If someone could show me how to do this, then it would save me having to mess around trying to get the syntax of my scripts correct.

---

### Post by oomingmak on 2007-07-07
I'm getting closer. 


I've just found this:

**[http://leuksman.com/pages/Linux#Nsurl](http://leuksman.com/pages/Linux#Nsurl)**

But I don't know if it would be suitable for Ubuntu (or if there might be thing in there that I would have to change to get it to work). 

The instructions are old (it keeps talking about 'Netscape') but there is some stuff in the readme about integrating it with KDE file manager (so it must also be possible for Nautilus).

I'm now convinced that what I'm trying to do is not only possible, but is trivial (provided that you are familiar with Linux - which I am not).

If anyone more experienced could give me (or point me to) a step by step instruction for this, I would be most grateful. The instructions in the Nsurl readme were way over my head.

Thanks.

---

### Post by Jose Catre-Vandis on 2007-07-07
OK

I have done a quick and dirty fix on the nsurl script that works from the command line when Firefox is open.
Copy this code to a text file and save as something like fxurl. 
```
#!/usr/bin/perl

# Open up the file
open(F,"<$ARGV[0]") or die "$0: Could not load Internet Shortcut file $ARGV[0]!\n";

# Find the URL
while($in = <F> and not $url) {
    chop($in);
    if($in =~ m/\s*URL\s*\=\s*\S*\s*\015*/) {
        $url = $in;
        $url =~ s/\s*URL\s*\=\s*//; # Filter out the beginning stuff
        $url =~ s/\s*\015+//; # Filter out the nasty DOS carriage return!
    }
}

    system "firefox $url &";# or die "$0: Could not open $netscape\n"
```

Make the file executable.
```
sudo chmod a+x fxurl
```

Copy file to /usr/bin
```
sudo cp fxurl /usr/bin/fxurl
```

With Firefox already open, open a terminal  in the directory in which you find your .url file, e.g. linuxhq.url, and type:
```
 ./fxurl linuxhq.url 
```

You should find your page has opened in a new tab.

The script needs to be converted to a bash script so that you can then use it in nautilus (I think) but this gets beyond me

---

### Post by oomingmak on 2007-07-07
Thank you so much for your kind help!

I followed your instructions and my test url files **do** open in Firefox (and thankfully in a new tab, not a new window)  :D    

I'm tantalising close to my goal now.

I did try to do an "Open With" on a url file and specify 'fxurl' (*nice re-name you did, by the way*) but Nautilus is not having any of it. When I click on the file it just says that it is executable and do I want to view it or run it.

Looking at the instructions that came with the original nsurl, the process for associating in KDE looks pretty straight forward (it's a GUI procedure that's built into the file manager) and this was back in 1998! Yet nearly 10 years later in Gnome, the simple process of making and editing file types is a still a nightmare that involves hacking around in system files.

I've tried to follow a few MIME type guides in order to set .url to be associated with fxurl. I used the XML data for .desktop as a template, and then inserted my newly created MIME type into /usr/share/mime/packages/freedesktop.org.xml, but so far all I've managed to do is end up breaking all my launcher and network shortcuts instead - lol.

Thank goodness for backups.

---

### Post by oomingmak on 2007-07-09
Grrrr! 

:mad:

So near .... and yet so far.

I have inched even closer to my goal, but I'm not quite there yet.

I didn't like the name that was showing up in the context menu of my .url files, so I made a symlink to the script and called it 'Web Browser' (as this looks much better in the context of a GUI).

After *hours* spent trying to figure out why Nautilus kept nagging me about risks to my system (from clicking on a non-executable plain text file :rolleyes:) I FINALLY managed to get the damned thing properly associated with the perl script. Prior to that, I had only got it working from a sub-menu entry of the url context menu (but it would just not work when clicking directly on the file).

I checked and re-checked my MIME types XML file and I decided to abandon the *application/x-mswinurl *(with plain text sub type) and instead I edited it to make the main mime type "*text/plain*"

I did an  [FONT=Fixedsys]*update-mime-database /usr/share/mime*[/FONT]  (which didn't seem to make any difference) so I restated X, and bingo! The web site opened in Firefox when I clicked on my url file.

All was well, except for the fact that it only worked on certain shortcut files and not others. 

I found out that as part of the script process, it seems to be cutting off the last character of the url. If the url contains a trailing slash, then all is well, but if not, then the script cuts off the last letter of the TLD. It still works (in the sense that Firefox does open a page) but obviously you just get a 404 rather than the web site that you wanted.

So all I need now is to get the script slightly amended so that it does not chop off the last character (because this not only causes problems with TLDs, but also with pages that end in .php or .asp etc).


If someone could help me amend the script quoted above (in [**post number 6**]("http://ubuntuforums.org/showthread.php?p=2982063&#post2982063"))  I'd not only be very grateful, but I'd also have **[COLOR=DarkOrchid]*finally*[/COLOR]** achieved my goal.

:D

---

### Post by psych787 on 2007-07-16
I guess I've noticed your post pretty late, but I posted this a while back:
[http://ubuntuforums.org/showthread.php?t=324517&highlight=mswinurl](http://ubuntuforums.org/showthread.php?t=324517&highlight=mswinurl)

One advantage of this is that it can be used to open .desktop as well, shortcutting KDE's cache feature.

---

### Post by oomingmak on 2007-07-16
I got mine working in the end (but only with the help of a programmer friend who could attempt to make sense of the regex command stuff). There was an incorrect command in the original script.
 
The line:  *chop($in);* 
 
Should be:  *chomp($in);* 
 
This fix stopped the script from cutting off the last character of certain urls.
 
I then 'associated' .urls with my script (I ended up creating a new MIME type for this, because trying to work with existing ones was giving me no end of grief). I also wanted to keep my .urls distinct from .desktop files. 
 
Finally I created a new icon (in a different colour) and assigned it to my newly created Mime type (so that I could tell the difference between .desktop and .url files at a glance). I got absolutely nowhere trying to do this manually (despite spending hours following various different instructions). Fortunately I discovered Assogiate, and this helped me to assign an icon in just a few seconds. 
 
My Internet shortcuts now work *exactly *as I want them to. I even have a little utility that will read .desktop files and open them in Firefox on Windows. 

So now I can create shortcuts on either platform, and open them on either platform (without caring what format the internet shortcuts are in).

[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/InternetShortcuts.png[/IMG]
 

I didn't come across your thread when I was searching for a solution to this problem. I only found a couple of other threads on the topic (which  came as quite a surprise to me, because I would have thought that there would be much *more *demand from people for a feature like this). 

However, the threads that I did manage to find were pretty useless, because they ended up with the conclusion that it was impossible to make Internet Explorer shortcut files work in Ubuntu (mainly because there were some people who thought that a single line of ***plain text*** starting with "url=" was some kind of impenetrable proprietary Microsoft format :roll: ). 

I just ignored those comments and went and created my own working solution instead.

---

### Post by psych787 on 2007-07-17
I just did a quick search on "windows url file" and my post wasn't there. Perhaps it was because I always spell MS Windows as Windoze (to distinguish from X-Windows). I've added a few keywords now to make it a little more searchable.

Thanks for helping me catch this! :cool:

---

### Post by bokl on 2007-08-27
oomingmak,
I've been searching and troubleshooting for multiple hours (!!!) to get a way to open .url files in Firefox by doubleclicking -- it seemed like such a small simple thing but turned into a nightmare. I was about to give up when I found this thread! Let me now quote you "I have inched even closer to my goal, but I'm not quite there yet." :-) That is, could you please explain in more detailed steps exactly how you got this to work, since you do seem to have it set up EXACTLY like how I want it. 

steps (please fill in details at  _____ ):

1. copy code __________ into text file, save (will the bash script in the thread by psych787 work as well here and also let me skip step 2. ?)
2. compile by entering this in the terminal ___________
3. create new MIME type by adding _________ to this file _______
( i understand how to open the file at usr/share/mime/packages/freedesktop.org.xml . I find the entries corresponding to *.url . But I can't understand what to edit... I must somewhere link it to Firefox? But I can't find a field to do that through... )

4. Any hints on getting the special icon would also be very appreciated.


As a total ubuntu newbie, I cannot at all understand understand why this functionality isn't built in when Ubuntus .desktop files seems to do almost exactly the same thing as .url files... Anyway, thanks for the great work you've put in to get this to work though.

---

### Post by oomingmak on 2007-08-29
> **bokl said:**
> oomingmak, I've been searching and troubleshooting for multiple **hours** (!!!) to get a way to open .url files in Firefox
Lucky you. I was searching for **days**, not just hours



> **bokl said:**
> it seemed like such a small simple thing but turned into a nightmare.  
That sums up much of my experience in Ubuntu. ](*,)
 


> **bokl said:**
> Could you please explain in more detailed steps exactly how you got this to work, since you do seem to have it set up EXACTLY like how I want it.
I'll do my best. 

I am a complete Linux noob too and I don't even really 'use' Linux at all (as I'm a full time Windows user). I just mess around with Linux on occasion (as preparation and practice in case I have to give up Windows in the future).

---

### Post by oomingmak on 2007-08-29
[COLOR=Black]The explanation of how I discovered the various pieces of the jigsaw puzzle (that [/COLOR][COLOR=Black]*finally *[/COLOR][COLOR=Black]allowed me to get .url files working on Linux) can be found in my earlier posts in this thread. However, below is a *summary* of the steps that I took to get it working. 

As I said before, I'm a complete novice when it comes to Linux, so my method might not be the most efficient way of providing this functionality, but no one else has come up with any kind of solution, and at least I know that my method definitely works.

Apologies if my instructions are a bit too simplistic, but you did say that you are a total noob, so I've tried not to make any assumptions about what you already know how to do on Linux. By keeping my instructions simple, it should hopefully make it easier for other newbies to [/COLOR][COLOR=Black]understand and [/COLOR][COLOR=Black]follow as well.[/COLOR]




[COLOR=Sienna][B][SIZE=5]
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG][/SIZE][/B][SIZE=5][SIZE=2][COLOR=White]- [/COLOR][/SIZE][/SIZE][B][SIZE=5]Steps to get .url internet shortcuts to open in Firefox on Ubuntu[/SIZE]


1.[/B][COLOR=Black] **Create**[B] a script file that can read and extract the web links contained within a .url file.
[/B]The following script is the one that I created (after much struggling) based on the 'nsurl' code that I found on the internet[/COLOR][/COLOR][COLOR=Black]. The version below [/COLOR][COLOR=Black]contains th[/COLOR]e [COLOR=Sienna][COLOR=Black]fix for the 'URL truncation' problem that was mentioned earlier in this thread.[/COLOR][/COLOR]

[COLOR=Black]Right-click on your Desktop and select 'Create Document' and then 'Empty File'. This will create a new blank text file. Open the file and paste the the script shown below into it. Save the file and name it:  *fx-url*[/COLOR][COLOR=Sienna][COLOR=Black]

```
#!/usr/bin/perl

# Script to make Microsoft Windows Internet Shortcuts (*.url) work on Linux. 

# Oomingmak fixed version. This script now works properly.
# It no longer cuts off the last character of the URL.

# Open up the file
open(F,"<$ARGV[0]") or die "$0: Could not load Internet Shortcut file $ARGV[0]!\n";

# Find the URL
while($in = <F> and not $url) {
    chomp($in);
    if($in =~ m/\s*URL\s*\=\s*\S*\s*\015*/) {
        $url = $in;
    $url =~ s/\s*URL\s*\=\s*//; # Filter out the beginning stuff
    $url =~ s/\s*\015+//; # Filter out the nasty DOS carriage return!
        
        
    }
}

    system "firefox $url &";# or die "$0: Could not open $netscape\n"

```[B] 
[COLOR=White]
.[/COLOR]
[COLOR=Sienna]2.[/COLOR] Make the script executable.[/B]
Once you have created and saved the script, you need to make it *executable* so that it can run like a program. To do this, open a command line terminal window and use the 'cd' command to change directory to where you have the script stored (for example:  *cd Desktop*) and then type: ```
sudo chmod a+x fx-url
```[/COLOR][/COLOR][COLOR=Sienna][B] 
[COLOR=White]
.[/COLOR]
3. [/B][COLOR=Black][B]Place the executable script into the /usr/bin folder.
[/B] You must have 'root' privileges in order to put anything in /usr/bin (because it's a system folder). This means that you must use the '*sudo*' command when issuing the file move instruction. Copy the command shown below and paste it into the terminal window: [/COLOR][/COLOR]```
[COLOR=Black]sudo mv fx-url /usr/bin/fx-url[/COLOR]
```[COLOR=Sienna][COLOR=Black] 
[COLOR=White]
.[/COLOR]
**[COLOR=Sienna]4. [/COLOR]Create a symlink to the executable script (in the same /user/bin folder). **
[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]   To create a symlink to the fx-url file, paste the following command into the terminal window: [/COLOR][/COLOR]```
sudo ln -s /usr/bin/fx-url /usr/bin/'Web Browser'
```[COLOR=Sienna][COLOR=Black]This symlink step is not essential, but it does allow you to specify the name that appears in the context menu when right-clicking on .url files (without having to mess with the name of the script itself). If you don't do this step, then when you right-click on an internet shortcut, instead of seeing a menu item that says "*Open with Web Browser*" you will instead just see "*fx-url*" (which is not very nice looking). Seeing as you are only renaming the symlink, you can choose whatever name you'd like to see in the context menu. Just replace the text 'Web Browser' (in the above command) with the name that you prefer.


[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black] 

**[COLOR=Sienna]5.[/COLOR] **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black][B]Create a Mime type to recognise .url files.
[/B][/COLOR][/COLOR][COLOR=Black]A 'mime type' must exist for each file type. Mime types are what the system uses to detect the presence of a certain type of file. We therefore need to create a mime type for .url files so that the system will be able to identify them in future. By far the easiest way to work with mime types is to use a program called AssoGiate.

If you are using Ubuntu 7.10 (Gutsy Gibbon) or later, you can easily install AssoGiate [/COLOR][COLOR=Black]by using the 'Add/Remove' item on the 'Applications' menu. Just search for [/COLOR][COLOR=DarkSlateGray]'[COLOR=Black]AssoGiate', install it, and then skip to step number 6. (Make sure that you have selected 'Show: All Available Applications'  in the 'Add / Remove' dialog, otherwise AssoGiate won't show up in the search results).

[/COLOR][/COLOR] [COLOR=Black]For earlier versions of Ubuntu, you will need to install AssoGiate from source code using the instructions below:[/COLOR][LIST]
[*][COLOR=Black]Install the libraries that are needed in order for AssoGiate to work.[/COLOR][COLOR=Sienna][COLOR=Black][COLOR=Black] You do this by pasting the following into a [/COLOR][/COLOR][/COLOR][COLOR=Sienna][COLOR=Black][COLOR=Black]command line terminal: [/COLOR][/COLOR][/COLOR]*> sudo aptitude install g++ libgtkmm-2.4-dev libgnome-vfsmm-2.6-dev libxml++2.6-dev gettext gnome-doc-utils*[/LIST][LIST]
[*][COLOR=Black]Download the AssoGiate installation package ([COLOR=Gray]*click the link* >>[/COLOR][/COLOR] _[[COLOR=Orange]**Download AssoGiate**[/COLOR]]("http://www.kdau.com/projects/assogiate/download.html")_[COLOR=Black]). [/COLOR][/LIST][LIST]
[*][COLOR=Black]Unpack the downloaded file and follow the 'Basic Install' instructions that are located in the file called INSTALL. [/COLOR][COLOR=Black]See my post[/COLOR] [_[COLOR=Orange]**here**[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=517198") [COLOR=Black]if you require more[/COLOR] [COLOR=Black]information.[/COLOR][/LIST][COLOR=Black]The installation puts an AssoGiate icon under your 'Applications' menu, [/COLOR][COLOR=Black]so you just go to *Applications > *[/COLOR]*[COLOR=Black]System Tools >  File Types Editor[/COLOR]*[COLOR=Black] and [/COLOR][COLOR=Black]run it from there whenever you need to make file type changes.[/COLOR]



  
[COLOR=Sienna][B]6. [COLOR=Black]Create a url file type.
[/COLOR][/B][/COLOR][COLOR=Black]Open AssoGiate. Click the 'New' button on the toolbar to create a new Mime type. Enter the settings exactly as they are shown below and then save your changes:[/COLOR]

[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/Screenshot-EditTypetext-x-url1.png[/IMG]
For the **Default Icon **setting (shown above), just use the browse button [COLOR=White].[/COLOR]  [IMG]http://i219.photobucket.com/albums/cc48/0omingmak/4339f6a3.png[/IMG]   [COLOR=White]. [/COLOR]to select any icon of your choosing.



[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/Screenshot-EditTypetext-x-url2.png[/IMG]




[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/Screenshot-EditTypetext-x-url3.png[/IMG]




[COLOR=Sienna][COLOR=Black]**[COLOR=Sienna]7. [/COLOR]**[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**Associate the executable script with the .url file type.**
Now that you've created a url mime type, your system knows how to *recognise* which files are url files, but it still doesn't know what it should *do* with them once it's identified them. We therefore have to associate the .url file type with the executable script that we made earlier. To do this, find any .url file, right-click on it and choose the 'Properties' menu. Go to the 'Open With' tab and press the 'Add' button. (An 'Add Application' window will appear). At the bottom of the Add Application window is an option called 'Use a custom command', click this option and browse to /user/bin and then select the symlink file that you created in step number[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black] [COLOR=Sienna][COLOR=Black]4[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Sienna][COLOR=Black] - [for example: /*usr/bin/Web Browser *]. Click the 'Add' button to save your changes.[B]



[COLOR=Sienna]8. [/COLOR]Make the associated action the default option.
[/B]If you don't specify a 'default' action, then your .url files won't be activated automatically when you click on them (you will instead always have to right-click the .url file and choose the required option from the context menu). To make opening in Firefox the default action, go back to the 'Open With' tab of any .url file (*Right-click on .url file > 'Properties' > 'Open With'*) and click the dot to the left of the entry that you just added (e.g. *Web Browser*). Next, open a Nautilus file manager window and go to the '[/COLOR][/COLOR][COLOR=Black]Edit' menu and select 'Preferences' then 'Behavior'. In the 'Executable Text Files' section, make sure that '*_View_ executable text files when they are clicked*' is selected[/COLOR][COLOR=Sienna][COLOR=Black]. 

To check that the default option change has worked properly, [/COLOR][/COLOR][COLOR=Black]restart X (by pressing: Ctrl + Alt + Backspace)[/COLOR][COLOR=Sienna][COLOR=Black] then log back in to your desktop and right-click on any .url file. You should now see the top entry of the .url context menu saying: ***Open with "Web Browser"**.*[/COLOR][/COLOR]

[COLOR=Black]Clicking a .url file should then automatically start Firefox and go to the specified web site. If Firefox is already running then the web page will just open in a new tab.
[/COLOR][COLOR=Black][B][SIZE=4][COLOR=Sienna] 

Done!

[/COLOR][/SIZE][/B][/COLOR]

---

### Post by oomingmak on 2007-08-29
> **bokl said:**
> Any hints on getting the special icon would also be very appreciated.

I just created my own icon for .url files by using the existing Ubuntu icon for web shortcuts (gnome-fs-bookmark.png), masking off the yellow arrow and then colour shifting it in Photoshop.

I think you can do the same in Gimp by using the Colourmap rotation filter.

If you can't be bothered to make you own, then you can use some that I created. I've attached them to this message. Just right-click and select 'Save Image As' to download them.



[COLOR=White]..[/COLOR]

---

### Post by bokl on 2007-08-30
First, thanks a lot for taking time to explain this! I appreciate it a lot!
There are not many smileys to choose from for this forum so I'll have to resort to show my gratitude by giving you a lot of popcorn: :popcorn: :popcorn: :popcorn: :popcorn:

I don't find the instruction simplistic. It's on the contrary perfect for my level. 

In step 4, I got a "Permission denied" message. Solved that by prepending sudo to the code, like this:
```
sudo ln -s /usr/bin/fx-url /usr/bin/'Web Browser'
```

I'm stuck at step 5-6: I can under properties for a .url add the Web Browser symlink, then select it in the list (actually its selected by default since I removed all other entries for .url). But after pressing "Close" the context menu of the .url does not reflect the change! And doubleclicking the .url gives and error. I can however right click the .url , select "open with other application", navigate to the Web Browser symlink (or just type 'Web Browser' in the custom command box). Then it works. But then I must repeat that every time.

Any ideas on what goes wrong?

**Edit:** 
I restarted X by pressing: Ctrl + Alt + Backspace. After that, I see "Web Browser" in the context menu for .url files. Great, I'll try the rest of the steps now...

I'm on step 8...
I carry out the basic instruction in the INSTALL file in the extracted Assogiate folder by:
- open terminal, navigate to the extracted Assogiate folder
- run this: 
```
./configure
make
sudo make install
```

I don't see any error messages in the terminal but there's no Assogiate entry in the Applications menu so something seems to have gone wrong.

**Edit2:** ...but I can press Alt + F2 , enter Assogiate , klick Run and then it opens so its only the entry on the menu that is missing... Let's see how the rest of the steps go now...
**Edit3:** almost done now! After finishing the last step and doubleclicking a .url file, I now get a warning popup dialog: "__.url is an executable text file." and the options Run in Terminal, Display, Cancel, Run. If I choose Display then it opens in Firefox. How do I set it to display as default?

---

### Post by oomingmak on 2007-08-30
> **bokl said:**
> 

In step 4, I got a "Permission denied" message. Solved that by prepending sudo to the code, like this:
```
sudo ln -s /usr/bin/fx-url /usr/bin/'Web Browser'
```Well spotted! (I was just testing that you were paying attention ..... ahem) :---)

I'm surprised that I made a mistake like that (seeing as I had already stated that writing to /usr/bin requires root privileges).

Anyway, I've now edited the post to add the sudo command. Thanks for pointing it out.

---

### Post by oomingmak on 2007-08-30
> **bokl said:**
> 

Edit2: ...but I can press Alt + F2 , enter Assogiate , klick Run and then it opens so its only the entry on the menu that is missing...
I don't know why that happened. Did you try showing the System Tools menu, just in case it put it in there? I can't remember exactly where it puts the launcher by default (because I moved mine shortly after I installed it). Of course it's easy enough to create a new launcher  (i.e. 'shortcut') just by pointing to:   */usr/local/bin/assogiate*


> **bokl said:**
> 

Edit3: almost done now! After finishing the last step and doubleclicking a .url file, I now get a warning popup dialog: "__.url is an executable text file." and the options Run in Terminal, Display, Cancel, Run. If I choose Display then it opens in Firefox. How do I set it to display as default?
Trouble shooting is not my forté (seeing as I am so inexperienced) so it's a bit like the blind leading the blind - lol.  :lolflag:

I do remember having a similar problem, but I can't remember how I fixed it. Try the following and see if it makes any difference:

Open a Nautilus file manager window, go to* [COLOR=Navy]Edit > Preferences > Behavior [/COLOR]*and then chose '[COLOR=Navy]*_View_ executable text files when they are clicked*[/COLOR]' under the '[COLOR=Navy]*Executable Text Files*[/COLOR]' section.

---

### Post by kdau on 2007-08-30
Hello oomingmak, it's the author of assoGiate again.

I just checked the standard database to see why this file type wasn't already there. It turns out that there is an application/x-mswinurl type listed, but it's missing a description and a "*.url" match, making it less than useful. If possible, I'd recommend moving your custom "*.url" match to this (more official) type name. When I get a chance, I'll submit a patch to the shared-mime-info maintainers to fill the type out properly.

I noticed that you put a call to update-mime-database in your instructions. assoGiate is supposed to do that itself, but I've had reports from other distros that this may not be happening consistently. Have you made changes in assoGiate that haven't taken effect until you ran update-mime-database manually? Any information would help me resolve that problem in the upcoming release.

---

### Post by oomingmak on 2007-08-30
> **kdau said:**
> Hello oomingmak, it's the author of assoGiate again.

I just checked the standard database to see why this file type wasn't already there. It turns out that there is an application/x-mswinurl type listed
Hi Kevin. Yes, I did see application/x-mswinurl while hunting around in [COLOR=Sienna][COLOR=Black]freedesktop.org.xml. I did try to use it at first (as I stated in [[COLOR=DarkOrange]**post number 8**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=2989014#post2989014") of this thread) but being a total novice (and having never had *any *experience of working with Mime types before) I had no idea why it wouldn't work for me.[/COLOR][/COLOR]

> **kdau said:**
> .... but it's missing a description and a "*.url" match, making it less than useful.
I did try to fix this when I was making my initial manual edits, but for some reason it just would not work (and I tried for ages!). However, as soon as I gave up on application/x-mswinurl and made my own mime type from scratch, I got my .url files working just fine. 

I'm not sure quite why this was (I did it a fair while ago and so I can't really remember all the steps that I took) but certainly using the existing x-mswinurl would have been my preferred route (had I been able to get it to work).

> **kdau said:**
>  When I get a chance, I'll submit a patch to the shared-mime-info maintainers to fill the type out properly.
Thanks. It would be great if this worked by default. The fix is trivial for the shared-mime-info maintainers to implement, but the rewards (especially for beginners) is significant. It does seem ridiculous that it should be such hard work just to get a web link shortcut to open (especially seeing as the .desktop format is virtually identical to .url files).

> **kdau said:**
> I noticed that you put a call to update-mime-database in your instructions. assoGiate is supposed to do that itself, but I've had reports from other distros that this may not be happening consistently. Have you made changes in assoGiate that haven't taken effect until you ran update-mime-database manually?
Oops! :oops: 

I think that the instruction to update the mime database may just have been a left-over from my earlier attempts when I was editing the XML file manually. I just forgot to take it out.

I can't say that I've had any problems with assoGiate changes not taking effect. The only problem I've had with assoGiate was with not being able to delete a binding to filename pattern (but I seem to recall you are already aware of this particular issue). Other than that, it's all been good :cool:

Thank you for creating such a useful program.

---

### Post by bokl on 2007-08-30
Hi again oomingmak
> Open a Nautilus file manager window, go to Edit > Preferences > Behavior and then chose 'View executable text files when they are clicked' under the 'Executable Text Files' section
Yes, now it works. Again, thank you so very much for taking time and helping me out with this. 

Also thanks to kdau for Assogiate which made this possible. 

Now I have a whole bunch of .urls to open so I'm signing out... :)

---

### Post by oomingmak on 2007-08-30
> **bokl said:**
> 

Hi again oomingmak. Yes, now it works.
Great news! :)

> **bokl said:**
> Again, thank you so very much for taking time and helping me out with this .... Now I have a whole bunch of .urls to open so I'm signing out...
And I think I'll go and make a start on all that popcorn ....

:popcorn:

---

### Post by bokl on 2007-08-30
I forgot to write one thing: I did find Assogiate on the applications menu in the end - it was at Applications > System Tools > File Types Editor. I looked so much for the text Assogiate that I missed it. So its all good now. :)

---

### Post by joewski on 2007-08-31
Hi everybody,

This is such a good fix. 

I'm migrating from windows, and it's not just not one machine, its the whole tribe.

I was wondering if this could be turned into a patch for Ubuntu to be installed standard or as a package? I've got a few machines to convert and was wondering how I could go about this? I think this would help many new users.

Any help for us **Windows migrants** would be greatly appreciated. 

Thanks.

---

### Post by oomingmak on 2007-08-31
> **joewski said:**
> Hi everybody,

This is such a good fix.
Thank you.


I still can't quite believe that an utterly clueless, absolute Linux noob like me could have come up with a fully working solution to this problem, when other more experienced users were saying that it could not be done. 

I did search the forum before starting this thread, but only 2 results came up (neither of which provided a solution).

[COLOR=DarkOrange]**[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG][COLOR=White]. [/COLOR]**[/COLOR][**[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=281123[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=281123") 

[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG] **[COLOR=White].[/COLOR]**[**[COLOR=DarkOrange]http://ubuntuforums.org/showthread.php?t=236913[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=236913")
[COLOR=DarkOrange][COLOR=Black]
Some of the comments in the first link are quite funny; things like:

"[/COLOR][/COLOR]*Why don't Windows .URL shortcuts work? the same reasons that you can't just run a .DLL or other windows file types like .EXE.*"

"*Why bother? just open up in text editor to show the full URL addy copy and paste it to linux firefox address bar*" 

I'm so glad that I didn't pay any attention to those 2 threads. I _knew_ that it must be possible (even though I didn't know exactly how) and so I just persevered until I ended up creating my own solution.

> **joewski said:**
> I was wondering if this could be turned into a patch for Ubuntu to be installed standard or as a package? I've got a few machines to convert and was wondering how I could go about this? I think this would help many new users.
Well, I'm sure that someone could very easily use my instructions to make a .deb file that would install the script (and make all the other necessary changes) so that adding this functionality would become a simple 1-click affair, but unfortunately that kind of thing is ***way ***beyond my capability.

Sorry. :(

---

### Post by oomingmak on 2007-09-04
Continuing the 'internet files' compatibility theme of this thread; I have now also managed to get my .mht archive collection working in Firefox Ubuntu.

I thought I'd mention it here just in case anyone else might be interested in doing the same (but doesn't know how to).



[[COLOR=DarkOrange]**MHT **[/COLOR]]("http://en.wikipedia.org/wiki/MHTML")is the format used by Internet Explorer to save a web / HTML page into a **single** file (or 'web archive') rather than creating an HTML text file plus a separate folder containing all of the page's images and other media.

It is *not* a Microsoft format (nor is it proprietary). It's actually based on an IETF [**[COLOR=DarkOrange]RFC standard[/COLOR]**[COLOR=Black].[/COLOR]]("http://tools.ietf.org/html/rfc2557")

Although Internet Explorer and Opera both natively support this standard, Firefox does not (and judging by how old the [[COLOR=DarkOrange]**bugzilla**[/COLOR][COLOR=DarkOrange]** request**[/COLOR]]("https://bugzilla.mozilla.org/show_bug.cgi?id=18764") is for this particular feature, I doubt that it ever will) but fortunately there's an extension that can provide .mht compatibility for Firefox. 

The MAF extension ([http://maf.mozdev.org](http://maf.mozdev.org)) *reads* Internet Explorer generated .mht files and can also* save* to that format as well (although its saved output is not always Internet Explorer compatible). Despite this, it's still useful to be able to view all your existing .mht web content, and any new .mht file that you create using MAF, will work fine in Firefox (even if it doesn't always open in Internet Explorer). You can always go back to saving in Firefox's built-in 'Web Page complete' format (i.e. standard HTML plus separate images) if you need to be absolutely sure of compatibility with IE.

Installing the MAF extension is not without it's problems though. The project now appears to have been abandoned and the most recent version of MAF (v0.6.3) does not work with v2.0.x of Firefox (it only works with Firefox up to v1.5.x). Fortunately this can be easily fixed by 'version bumping' the extension's install package.

To get your .mht files working in Ubuntu, do the following:




[COLOR=Sienna]**[SIZE=5][IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG][/SIZE]**[SIZE=5][COLOR=White].[/COLOR][/SIZE][B][SIZE=5]Steps to get [COLOR=DarkRed].mht[/COLOR] files to open in Firefox on Ubuntu

[SIZE=2]1.  [/SIZE][/SIZE][/B][SIZE=5][COLOR=Black][SIZE=2]**Download the MAF extension.**
_RIGHT_-click the following link and choose '*Save link As*...' to save the MAF extension to your Desktop. Don't left-click the link directly, or it will try to install itself into Firefox straight away (which won't work). 

Right-click and save >> [[COLOR=DarkOrange]**maf-0.6.3.xpi**[/COLOR]]("http://downloads.mozdev.org/maf/maf-0.6.3.xpi")


[COLOR=Sienna]** 2.**[/COLOR] **Patch the extension to make it compatible with version 2.x of Firefox.**
Click on the .xpi file to open it. It should automatically open in File Roller (the archive manager). Once opened, you'll see several files and folders inside the .xpi file. Right-click on the '*install.rdf*' file and extract it to your Desktop.

Open the .rdf file in a text editor and look for the line that says: [I]"[COLOR=SlateGray]<em:maxVersion>[COLOR=SlateGray]1.5[/COLOR]</em:maxVersion>[/COLOR]".

[/I]Change the value from 1.5 to 2.5 and then save the file. Now add the edited install.rdf file back into the .xpi file (either use File Roller's '*Add Files*' toolbar button, or just drag the file and drop it onto the open File Roller window). Close the File Roller window and then click on the maf-0.6.3.xpi again to re-open it. Click on the [/SIZE][/COLOR][/SIZE][/COLOR][COLOR=Sienna][SIZE=5][COLOR=Black][SIZE=2]install.rdf [/SIZE][/COLOR][/SIZE][/COLOR][COLOR=Sienna][SIZE=5][COLOR=Black][SIZE=2]file, and check that the version number change that you just made has been successfully retained.


**[COLOR=Sienna] 3.[/COLOR]** **Install the modified extension.**
Now install the MAF extension, by dragging the maf-0.6.3.xpi file onto an open Firefox window. Once it's installed, re-start Firefox.


**[COLOR=Sienna] 4.[/COLOR]** [B]Configure MAF
[/B]In Firefox, go to: *Tools > Mozilla Archive Format > Preferences* and select the '*Advanced Options*' tab. Untick the '*Alert on single page archive complete*' option then click the 'Save' button to save the change.


**[COLOR=Sienna] 5.[/COLOR]** [B]Create a MIME type to recognise the .mht files.
[/B]Use the Assogiate program (as mentioned earlier in this thread) to create a mime type for .mht files. The rfc822 mime type used by .mht files is already listed in the standard database as  'email message', so I've decided to create a new mime type for .mht so that it could have it's own associated actions and icon without interfering with any existing associations or file types. It also makes it easier to cleanly remove your customisations (if need be) without affecting any default settings. (Let's hope that Kdau doesn't tell me off for my non-standard mime type shenanigans -  :D) 

In Assogiate, use the 'New' button to create a blank mime type. Enter the options, listed below, into the corresponding tabs:

[B][IMG]http://www.ubuntu.com/products/casestudies[/IMG]&#9658; General tab:
[/B][COLOR=Silver]Category: [COLOR=Black]Messages[/COLOR][/COLOR]
[COLOR=Silver]Name:[/COLOR] [/SIZE][/COLOR][/SIZE][/COLOR][COLOR=Sienna][SIZE=5][COLOR=Black][SIZE=2]web-archive[/SIZE][/COLOR][/SIZE][/COLOR]
[COLOR=Sienna][SIZE=5][COLOR=Black][SIZE=2] [COLOR=Silver] Description:  [/COLOR]MHT Web Archive


[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/203b5ee3.png[/IMG]

Use the Browse button   [COLOR=White].[/COLOR] [IMG]http://i219.photobucket.com/albums/cc48/0omingmak/4339f6a3.png[/IMG][IMG]http://ubuntuforums.org/%5BIMG%5Dhttp://i219.photobucket.com/albums/cc48/0omingmak/efdd2b59.png%5B/IMG%5D[/IMG]  [COLOR=White].[/COLOR] to select an icon of your choosing for the .mht file type.


**&#9658; Related Types tab:**
[COLOR=Silver] Parent types:[/COLOR]  message/rfc822
  

**&#9658; Filenames tab**
[COLOR=Silver] Filename pattern:[/COLOR]  *.mht


[B]&#9658; File contents tab
[/B]The settings shown below have been provided further down the page as copyable text (to save you from having to manually type each entry). 

[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/51152123.png[/IMG]



[/SIZE][/COLOR][/SIZE][/COLOR][COLOR=Sienna][SIZE=5][COLOR=Black][SIZE=2][COLOR=Silver]Value:[/COLOR]  From: <Saved by
[COLOR=Silver]Value:[/COLOR] Content-Type: multipart/related;
[COLOR=Silver] Value: [/COLOR]boundary="----=_NextPart_
[COLOR=Silver]Value: [/COLOR] <!DOCTYPE HTML PUBLIC "-//W3C//DTD


[COLOR=Sienna]**6.**[/COLOR] [B]Associate .mht files with Firefox
[/B]Right-click on an .mht file and select 'Properties' and go to the 'Open With' tab. Click the 'Add' button and select 'Firefox Web Browser' from the list of programs that appears. Press the Add button again and close the dialog. 

Restart X (if necessary) by [/SIZE][/COLOR][/SIZE][/COLOR][COLOR=Black]pressing: Ctrl + Alt + Backspace.


[/COLOR][COLOR=Black][B][SIZE=4][COLOR=Sienna] Done!



[/COLOR][/SIZE][/B][/COLOR][COLOR=Gray](see the next post for some notes regarding certain MAF issues).[/COLOR]

---

### Post by oomingmak on 2007-09-04
**Some issues regarding the MAF extension:** 

1. The MAF plugin has always been a bit rough at the edges and it never got anywhere near doing as good a job as Internet Explorer of saving web pages as single files. These shortcomings were tolerated by users because there was simply no alternative for Firefox. So you may possibly encounter some incorrect layouts  when trying to save particularly complex (or strangely laid out) web pages using MAF. This problem is due to the MAF extension itself, rather than the method in which it was made to work on Ubuntu.

2.  You may experience a delay when opening large .mht files that were created by Internet Explorer. Depending on how slow your computer is, this delay could last up to 15 seconds before the page opens, so don't assume straight away that Firefox has locked up. You tend not to get any delays when opening .mht files that were created by MAF itself.

3. Running this MAF extension on v2.x of Firefox (when it was intended for use on v1.5x of Firefox) does have one side effect of opening a blank tab in addition to the tab containing your .mht content. Often the blank tab is focussed (because it opens first) so it may look as if the file was corrupt and didn't open. But if you look to the right of the blank tab, you should see a tab showing your .mht content. I tried to find a workaround for this issue, but I have been unable to.

While the above situation is not ideal, it's still perfectly usable for both reading and writing of .mht files in Linux.

You could of course always ditch Firefox and switch to [**[COLOR=DarkOrange]Opera[/COLOR]**]("http://www.opera.com/") (which has full *native *.mht compatibility) if .mht compatibilty is that important to you. If you do decide to use Opera as your web browser, then simply ignore all the above instruction steps relating to the MAF extension, and just follow the instructions in Step 5. For Step 6, you obviously would select Opera for 'Open With' instead of selecting Firefox.

I don't use Opera myself, but my method has been shown to work just fine with it (see >> [**[COLOR=DarkOrange]Here[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=495625") << for details).

I hope this info has helped some people out.

---

### Post by psych787 on 2007-09-28
Wow... haven't checked these forums in a while - I thought my topics were dead! MHT file support is something I never even considered :D. Thanks!

---

### Post by oomingmak on 2007-09-29
> **psych787 said:**
> MHT file support is something I never even considered. Thanks!
You're welcome.

:)

---

### Post by bsmith1051 on 2007-10-02
> **joewski said:**
> I was wondering if this could be turned into a patch for Ubuntu to be installed standard or as a package? I've got a few machines to convert and was wondering how I could go about this? I think this would help many new users.
This absolutely would help a lot of people.  Can we start a petition or something to add this?

---

### Post by oomingmak on 2007-10-03
> **bsmith1051 said:**
> This absolutely would help a lot of people.  Can we start a petition or something to add this?
I agree that providing this functionality as a patch would be useful, but I have no idea who should be approached to make such a request.

---

### Post by oomingmak on 2007-10-04
**@**[B] [COLOR=Black]bsmith1051

[/COLOR][/B][COLOR=Black]I've only just realised that you were the originator of one of the [**[COLOR=DarkOrange]posts[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=281123") that I linked to above (that was asking for a way to use .url files in Ubuntu).

I notice that by the end of the thread (after several rather unhelpful responses to your posts) there was still no resolution to the issue that you raised, and so I was wondering what you did for a solution in the interim? [/COLOR][COLOR=Black]As there was no documented method or patch available, [/COLOR][COLOR=Black]did you manage to get it working by yourself?

The reason that I ask is because your thread was from a year ago, and it does make me wonder how many other people would also have liked to have such a feature, but would have [/COLOR][COLOR=Black]just [/COLOR][COLOR=Black]given up  on it after having seen threads on here implying that it was impossible to do.

I'm not sure whether any of these people would [/COLOR][COLOR=Black]then [/COLOR][COLOR=Black]have managed to devise their own methods to get it working, because the solution is not exactly intuitive for beginners (it took me weeks to figure out). So a patch or package could be a real benefit to people in a similar situation (especially if they need it to be applied to multiple PCs). 

If I had a clue what I was doing in Linux, then I would make it myself, but as I said previously, [/COLOR][COLOR=Black]creating something like that is[/COLOR][COLOR=Black] unfortunately way beyond my capabilities.

[/COLOR]

---

### Post by bokl on 2007-10-20
Just a small update on step 8 in Oomingmak's "Steps to get .url files to open in Firefox on Ubuntu" earlier in this thread:
Assogiate doesn't seem to be included in Ubuntu 7.10 (gutsy gibbon) after all so this step is still needed. But it can now be installed more easily: Goto Applications > Add/Remove... and search for "File Types Editor" and install that.


Also, since there's a few of us here who persist in wanting .url files to work by default, can anyone advise on the most effective way to get our voice heard by the ones able to include or not include it in the next Ubuntu this spring? Should a request be submitted somewhere and people add votes to it?

One more thing: what is the best place in the system to store customized icons? At the moment I put them in a folder on the desktop but I sense that it would be better to place them somewhere out of sight and not related to a specific user account in the way the desktop is.

---

### Post by kdau on 2007-10-20
> Assogiate doesn't seem to be included in Ubuntu 7.10 (gutsy gibbon) after all so this step is still needed.

I'm sorry, I was unclear about what inclusion meant. Yes, assoGiate is included in 7.10, meaning that you can install it from Add/Remove. Being part of the bundled software automatically installed with the upgrade is a much steeper climb, and not really appropriate for assoGiate anyway.

> ...can anyone advise on the most effective way...

The MIME type data for .url and .mht files need to be submitted to the shared-mime-info people. I'm going to do that myself as soon as I clear my backlog.

oomingmak's .url-parsing script and the MAF Firefox extension would need to be distributed as Ubuntu packages, with the proper open-with associations in their .desktop files. This process could be started by filing Launchpad bugs requesting the packages, but given their obscurity it might be better to submit prepared source packages. When I have more time, I'll look at both to see how suitable they are for packaging.

> One more thing: what is the best place in the system to store customized icons?

The next version of assoGiate (delayed, but in progress) will improve the storage of custom icons. Instead of making links to where icons are already stored, the program will copy them to the proper icon directory. If editing the system file types database (via sudo), the icons will be in a system-wide directory. You won't need to keep the originals around.

---

### Post by bokl on 2007-10-20
kdau, thanks for the answers! I hope you keep us updated if there's anything (non-coding) we can do to help.

everyone, Perhaps I spoke too hastily earlier. When I followed all of oomingmaks steps (apart from the changed installation of Assogiate/File Types Editor that I described) in 7.10 just now I still can't get .urls to open in Firefox. Nothing seems to happen. I've rebooted twice. Weird since it worked fine in 7.04. Anyone else having problems with this in 7.10?

---

### Post by oomingmak on 2008-01-03
> **bokl said:**
> When I followed all of oomingmak's steps using [Ubuntu] 7.10 just now, I still can't get .urls to open in Firefox. Nothing seems to happen. I've rebooted twice. Weird since it worked fine in 7.04. Anyone else having problems with this in 7.10?


Hi Bokl, did you ever manage to resolve your problem getting your urls working again after you upgraded versions?

Unfortunately I can't comment about how my instructions work on Ubuntu 7.10, because I never used 7.10 long enough to find out (it was just too unstable for me).

However, I have recently tried out Linux Mint v4.0 (which is based on Ubuntu 7.10 / Gutsy) and strangely that runs fine on my system. One of the first things I did after installing Mint was to set-up url associations, and it all worked without any problems at all. 

So I can at least say that as far as Linux Mint goes there's no problem here (if that's any help to you) which does seem to suggest that your issue might be specific to your computer.

---

### Post by David_1cog on 2008-01-22
First, thanks to oomingmak for pulling this together.  I was searching for a solution to this problem a year ago and eventually gave up (after useful advice similar to "edit the URL file, copy and paste url to browser"!).

This functionality is near crucial for many people hoping to migrate from Windows.  I have hundreds, maybe thousands of .URLs, and if I couldn't open them easily, I couldn't move to Ubuntu.  

> **kdau said:**
> When I get a chance, I'll submit a patch to the shared-mime-info maintainers to fill the type out properly.

kdau,  did you get chance to do that?  I'm running 8.04 and the description is still missing.


I've raised a bug for this issue - [https://bugs.launchpad.net/ubuntu/+bug/185165](https://bugs.launchpad.net/ubuntu/+bug/185165).  If anyone wishes to voice support, please add your comment.

---

### Post by oomingmak on 2008-01-22
> **David_1cog said:**
> First, thanks to oomingmak for pulling this together.
Glad to be able to help.



> **David_1cog said:**
> I was searching for a solution to this problem a year ago and eventually gave up.
Well it's good that you managed to find this thread and finally get the solution that you were looking for.



With regards to your comment directed to Kdau, he has not been on this forum since October. I know that he does spend time working away from F/OSS, so he might not have had time to make the submission to the shared-mime-info people.

However, maybe your Launchpad bug will get the attention of a developer who can get this issue resolved.

---

### Post by K.Morgan on 2008-04-13
Firstly i would like to say that this thread has been an absolute life saver, and why this is not built into Ubuntu as standard I will never know.  Using urls made in either Windows or an Apple mac work with each other why not in Linux?

Anyway followed your instructions and everything works fine, but I have a problem.  When I double click the url it continues to load Firefox but firefox never comes to the front of the screen it will always load behind the open folder I've just linked the link from.  Is there any way to bring firefox to the front of the screen after clicking a URL automatically?

Kristian

---

### Post by bsmith1051 on 2008-04-13
> **K.Morgan said:**
> Is there any way to bring firefox to the front of the screen after clicking a URL automatically?
There's probably an option in Firefox to make it do this but it might cause more problems than it solves.  What you're referring to is called 'focus' and you want FF to grab focus on new links; most people hate it when their browser does this.

You might try editing the Preference under Tabs for "New Link Opens In..." and set it to New Window.  Not sure if that will grab focus, though.  You can check _all_ the settings by typing the URL, about:config, in the FF address box.  Try typing 'focus' into the Filter sub-window and you'll see about 10 advanced options -- not sure if any of them will do what you want, though.

---

### Post by oomingmak on 2008-04-14
[quote=K.Morgan]i would like to say that this thread has been an absolute life saver[/quote]

Thanks. It's nice to know that my thread is useful and still helping people.  :)

---

### Post by K.Morgan on 2008-04-14
> **bsmith1051 said:**
> There's probably an option in Firefox to make it do this but it might cause more problems than it solves.  What you're referring to is called 'focus' and you want FF to grab focus on new links; most people hate it when their browser does this.

You might try editing the Preference under Tabs for "New Link Opens In..." and set it to New Window.  Not sure if that will grab focus, though.  You can check _all_ the settings by typing the URL, about:config, in the FF address box.  Try typing 'focus' into the Filter sub-window and you'll see about 10 advanced options -- not sure if any of them will do what you want, though.

Thanks, I was hoping it would be something simple but obviously not.  Think i'll leave it for now, i'm sure there will be a solution somewhere soon.

Kristian

---

### Post by DavidONE on 2008-04-14
Try checking about:config and 'browser.tabs.loadDivertedInBackground' - you will want this set to 'false'.

---

### Post by K.Morgan on 2008-04-14
Thanks DavidONE, but just checked and it's already set to false.


Kristian

---

### Post by Tomcraft on 2008-05-05
> **oomingmak said:**
> [COLOR=Black]The explanation of how I discovered the various pieces of the jigsaw puzzle (that [/COLOR][COLOR=Black]*finally *[/COLOR][COLOR=Black]allowed me to get .url files working on Linux) can be found in my earlier posts in this thread. However, below is a *summary* of the steps that I took to get it working. 

As I said before, I'm a complete novice when it comes to Linux, so my method might not be the most efficient way of providing this functionality, but no one else has come up with any kind of solution, and at least I know that my method definitely works.

Apologies if my instructions are a bit too simplistic, but you did say that you are a total noob, so I've tried not to make any assumptions about what you already know how to do on Linux. By keeping my instructions simple, it should hopefully make it easier for other newbies to [/COLOR][COLOR=Black]understand and [/COLOR][COLOR=Black]follow as well.[/COLOR]




[COLOR=Sienna][B][SIZE=5]
[IMG]http://ubuntuforums.org/images/icons/icon2.gif[/IMG][/SIZE][/B][SIZE=5][SIZE=2][COLOR=White]- [/COLOR][/SIZE][/SIZE][B][SIZE=5]Steps to get .url internet shortcuts to open in Firefox on Ubuntu[/SIZE]


1.[/B][COLOR=Black] **Create**[B] a script file that can read and extract the web links contained within a .url file.
[/B]The following script is the one that I created (after much struggling) based on the 'nsurl' code that I found on the internet[/COLOR][/COLOR][COLOR=Black]. The version below [/COLOR][COLOR=Black]contains th[/COLOR]e [COLOR=Sienna][COLOR=Black]fix for the 'URL truncation' problem that was mentioned earlier in this thread.[/COLOR][/COLOR]

[COLOR=Black]Right-click on your Desktop and select 'Create Document' and then 'Empty File'. This will create a new blank text file. Open the file and paste the the script shown below into it. Save the file and name it:  *fx-url*[/COLOR][COLOR=Sienna][COLOR=Black]

```
#!/usr/bin/perl

# Script to make Microsoft Windows Internet Shortcuts (*.url) work on Linux. 

# Oomingmak fixed version. This script now works properly.
# It no longer cuts off the last character of the URL.

# Open up the file
open(F,"<$ARGV[0]") or die "$0: Could not load Internet Shortcut file $ARGV[0]!\n";

# Find the URL
while($in = <F> and not $url) {
    chomp($in);
    if($in =~ m/\s*URL\s*\=\s*\S*\s*\015*/) {
        $url = $in;
    $url =~ s/\s*URL\s*\=\s*//; # Filter out the beginning stuff
    $url =~ s/\s*\015+//; # Filter out the nasty DOS carriage return!
        
        
    }
}

    system "firefox $url &";# or die "$0: Could not open $netscape\n"

```[B] 
[COLOR=White]
.[/COLOR]
[COLOR=Sienna]2.[/COLOR] Make the script executable.[/B]
Once you have created and saved the script, you need to make it *executable* so that it can run like a program. To do this, open a command line terminal window and use the 'cd' command to change directory to where you have the script stored (for example:  *cd Desktop*) and then type: ```
sudo chmod a+x fx-url
```[/COLOR][/COLOR][COLOR=Sienna][B] 
[COLOR=White]
.[/COLOR]
3. [/B][COLOR=Black][B]Place the executable script into the /usr/bin folder.
[/B] You must have 'root' privileges in order to put anything in /usr/bin (because it's a system folder). This means that you must use the '*sudo*' command when issuing the file move instruction. Copy the command shown below and paste it into the terminal window: [/COLOR][/COLOR]```
[COLOR=Black]sudo mv fx-url /usr/bin/fx-url[/COLOR]
```[COLOR=Sienna][COLOR=Black] 
[COLOR=White]
.[/COLOR]
**[COLOR=Sienna]4. [/COLOR]Create a symlink to the executable script (in the same /user/bin folder). **
[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]   To create a symlink to the fx-url file, paste the following command into the terminal window: [/COLOR][/COLOR]```
sudo ln -s /usr/bin/fx-url /usr/bin/'Web Browser'
```[COLOR=Sienna][COLOR=Black]This symlink step is not essential, but it does allow you to specify the name that appears in the context menu when right-clicking on .url files (without having to mess with the name of the script itself). If you don't do this step, then when you right-click on an internet shortcut, instead of seeing a menu item that says "*Open with Web Browser*" you will instead just see "*fx-url*" (which is not very nice looking). Seeing as you are only renaming the symlink, you can choose whatever name you'd like to see in the context menu. Just replace the text 'Web Browser' (in the above command) with the name that you prefer.


[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black] 

**[COLOR=Sienna]5.[/COLOR] **[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black][B]Create a Mime type to recognise .url files.
[/B][/COLOR][/COLOR][COLOR=Black]A 'mime type' must exist for each file type. Mime types are what the system uses to detect the presence of a certain type of file. We therefore need to create a mime type for .url files so that the system will be able to identify them in future. By far the easiest way to work with mime types is to use a program called AssoGiate.

If you are using Ubuntu 7.10 (Gutsy Gibbon) or later, you can easily install AssoGiate [/COLOR][COLOR=Black]by using the 'Add/Remove' item on the 'Applications' menu. Just search for [/COLOR][COLOR=DarkSlateGray]'[COLOR=Black]AssoGiate', install it, and then skip to step number 6. (Make sure that you have selected 'Show: All Available Applications'  in the 'Add / Remove' dialog, otherwise AssoGiate won't show up in the search results).

[/COLOR][/COLOR] [COLOR=Black]For earlier versions of Ubuntu, you will need to install AssoGiate from source code using the instructions below:[/COLOR][LIST]
[*][COLOR=Black]Install the libraries that are needed in order for AssoGiate to work.[/COLOR][COLOR=Sienna][COLOR=Black][COLOR=Black] You do this by pasting the following into a [/COLOR][/COLOR][/COLOR][COLOR=Sienna][COLOR=Black][COLOR=Black]command line terminal: [/COLOR][/COLOR][/COLOR]**[/LIST][LIST]
[*][COLOR=Black]Download the AssoGiate installation package ([COLOR=Gray]*click the link* >>[/COLOR][/COLOR] _[[COLOR=Orange]**Download AssoGiate**[/COLOR]]("http://www.kdau.com/projects/assogiate/download.html")_[COLOR=Black]). [/COLOR][/LIST][LIST]
[*][COLOR=Black]Unpack the downloaded file and follow the 'Basic Install' instructions that are located in the file called INSTALL. [/COLOR][COLOR=Black]See my post[/COLOR] [_[COLOR=Orange]**here**[/COLOR]_]("http://ubuntuforums.org/showthread.php?t=517198") [COLOR=Black]if you require more[/COLOR] [COLOR=Black]information.[/COLOR][/LIST][COLOR=Black]The installation puts an AssoGiate icon under your 'Applications' menu, [/COLOR][COLOR=Black]so you just go to *Applications > *[/COLOR]*[COLOR=Black]System Tools >  File Types Editor[/COLOR]*[COLOR=Black] and [/COLOR][COLOR=Black]run it from there whenever you need to make file type changes.[/COLOR]



  
[COLOR=Sienna][B]6. [COLOR=Black]Create a url file type.
[/COLOR][/B][/COLOR][COLOR=Black]Open AssoGiate. Click the 'New' button on the toolbar to create a new Mime type. Enter the settings exactly as they are shown below and then save your changes:[/COLOR]

[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/Screenshot-EditTypetext-x-url1.png[/IMG]
For the **Default Icon **setting (shown above), just use the browse button [COLOR=White].[/COLOR]  [IMG]http://i219.photobucket.com/albums/cc48/0omingmak/4339f6a3.png[/IMG]   [COLOR=White]. [/COLOR]to select any icon of your choosing.



[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/Screenshot-EditTypetext-x-url2.png[/IMG]




[IMG]http://i219.photobucket.com/albums/cc48/0omingmak/Screenshot-EditTypetext-x-url3.png[/IMG]




[COLOR=Sienna][COLOR=Black]**[COLOR=Sienna]7. [/COLOR]**[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black]**Associate the executable script with the .url file type.**
Now that you've created a url mime type, your system knows how to *recognise* which files are url files, but it still doesn't know what it should *do* with them once it's identified them. We therefore have to associate the .url file type with the executable script that we made earlier. To do this, find any .url file, right-click on it and choose the 'Properties' menu. Go to the 'Open With' tab and press the 'Add' button. (An 'Add Application' window will appear). At the bottom of the Add Application window is an option called 'Use a custom command', click this option and browse to /user/bin and then select the symlink file that you created in step number[/COLOR][/COLOR][COLOR=Sienna][COLOR=Black] [COLOR=Sienna][COLOR=Black]4[/COLOR][/COLOR][/COLOR][/COLOR][COLOR=Sienna][COLOR=Black] - [for example: /*usr/bin/Web Browser *]. Click the 'Add' button to save your changes.[B]



[COLOR=Sienna]8. [/COLOR]Make the associated action the default option.
[/B]If you don't specify a 'default' action, then your .url files won't be activated automatically when you click on them (you will instead always have to right-click the .url file and choose the required option from the context menu). To make opening in Firefox the default action, go back to the 'Open With' tab of any .url file (*Right-click on .url file > 'Properties' > 'Open With'*) and click the dot to the left of the entry that you just added (e.g. *Web Browser*). Next, open a Nautilus file manager window and go to the '[/COLOR][/COLOR][COLOR=Black]Edit' menu and select 'Preferences' then 'Behavior'. In the 'Executable Text Files' section, make sure that '*_View_ executable text files when they are clicked*' is selected[/COLOR][COLOR=Sienna][COLOR=Black]. 

To check that the default option change has worked properly, [/COLOR][/COLOR][COLOR=Black]restart X (by pressing: Ctrl + Alt + Backspace)[/COLOR][COLOR=Sienna][COLOR=Black] then log back in to your desktop and right-click on any .url file. You should now see the top entry of the .url context menu saying: ***Open with "Web Browser"**.*[/COLOR][/COLOR]

[COLOR=Black]Clicking a .url file should then automatically start Firefox and go to the specified web site. If Firefox is already running then the web page will just open in a new tab.
[/COLOR][COLOR=Black][B][SIZE=4][COLOR=Sienna] 

Done!

[/COLOR][/SIZE][/B][/COLOR]

Hi oomingmak,

thx for this excellent tutorial!

one little question. I use hardy heron and don't get the icon to show up. Can you confirm this in hardy?
funny thing that the search result in tracker does show the icon I supplied in assogiate (see attached screenshot). Very, very strange...

kind regards 

Torsten Krüger

---

### Post by me.zho on 2008-05-06
> **oomingmak said:**
> 
```

    system "firefox $url &";# or die "$0: Could not open $netscape\n"

```


Should not you use "gnome-open" instead of "firefox"?

---

### Post by oomingmak on 2008-05-09
> **Tomcraft said:**
> Hi oomingmak, 

thx for this excellent tutorial!
I'm glad you liked it.


> **Tomcraft said:**
> One little question. I use hardy heron and don't get the icon to show up. Can you confirm this in hardy?
Funny thing that the search result in tracker does show the icon I supplied in assogiate (see attached screenshot). Very, very strange...

I'm not sure that I will be able to help you because, as I previously pointed out in my instruction guide, I am not experienced with Ubuntu (or Linux in general). Also, I haven't used Linux for quite a while, so the last version of Ubuntu I used was 7.10. I therefore can't say whether what you're seeing is an 8.04 specific issue or not. 

However, the fact that you get the correct icon in Tracker suggests that Assogiate has done it's job properly and that it's just Nautilus playing up with regards to icon display. So you could try updating the system icon cache to see if that fixes the problem (I can't guarantee that this will help though).


Run the following command in the terminal window and then restart X (or just reboot your machine if you prefer) and see if it makes a difference
```
sudo update-mime-database /usr/share/mime/
```

---

