---
title: "How to have all application windows maximized upon opening? - Ubuntu 18.04"
date: 2018-05-16
forum: General Help
---

### Post by tellapu on 2018-05-16
Hello!
Is there a way in Ubuntu 18.04 Bionic Beaver to have the windows of (all) opening applications maximized?
Or even better is there a way to have the system save the last window size and position?
Some application windows like Firefox, Evolution, Thunderbird, LibreOffice, gedit open maximized without problems, but other apps like evince, compiz settings manager don't open maximized. 
All solutions that worked in the past (namely Compiz Settings Manager/Place Windows options) don't work. 
Any tip is much appreciated, especially for evince.
Cheers!

---

### Post by tellapu on 2018-05-26
):P Is there anybody who could help with this? It would much appreciated!

---

### Post by kerry_s on 2018-05-26
```
sudo apt install devilspie2
```

most windows remember they are maximized, so you just need to do the 1's that don't remember.
i'll give you my list to start you off. the window class can be found with xprop.

gedit ~/.config/devilspie2/maximize.lua

```
if (get_window_class()=="Gnome-terminal") then
   maximize();
end

if (get_window_class()=="Stremio") then
   maximize();
end

if (get_window_class()=="Gnome-tweaks") then
   maximize();
end


```

---

### Post by tellapu on 2018-05-26
Thanks for the tip! Is there no solution without installing another app? 
In the past I read people having problems with devilpie.

---

### Post by kerry_s on 2018-05-26
devilspie, is dead.
devilspie2 is a new rewritten app that serves the same purpose.

for your evince just add to the list, copy & paste.

```

if (get_window_class()=="Evince") then
   maximize();
end

```

i haven't had any problems.

you also need to add-> devilspie2 <- to startup.

[ATTACH=CONFIG]279858[/ATTACH]

---

### Post by dragonfly41 on 2018-05-26
A gui for this is x-tile (in Software Centre).

---

### Post by tellapu on 2018-05-28
**@[[B][COLOR=#000000]kerry_s[/COLOR]**]("https://ubuntuforums.org/member.php?u=132335") [/B][**[COLOR=#000000][/COLOR]**]("https://ubuntuforums.org/member.php?u=132335")Thank you for the further information. 
@[**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878") Thank you for the tip regarding x-tile but I can not find it in the Ubuntu Software Center in 18.04 nor in Synaptic Package Manager. It looks like it is not an official package anymore but there is a PPA: [https://askubuntu.com/questions/1029202/how-to-install-x-tile-on-ubuntu-mate-18-04-lts](https://askubuntu.com/questions/1029202/how-to-install-x-tile-on-ubuntu-mate-18-04-lts)

---

### Post by tellapu on 2018-05-28
@[**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878")  I could install x-tile but I don't understand how x-tile can automatically maximize all or certain apps upon opening (without always needing to click "maximize" in x-tile). Help is not available anymore ([http://www.giuspen.com/x-tile/](http://www.giuspen.com/x-tile/)), it seems that since 2016 this app is abandoned. Any tip to have x-tile remember which app to automatically maximize the window upon opening?

---

### Post by dragonfly41 on 2018-05-29
The developer of x-tile has to support multiple projects. I use cherrytree from his site.

Looking again only at evince you have many options through command line.

[https://help.gnome.org/users/evince/stable/commandline.html.en](https://help.gnome.org/users/evince/stable/commandline.html.en)

For example you can write a short bash script or python script to launch one or more pdf files
in full screen mode or other modes.

```

cd ~/Documents
evince --fullscreen three-column.pdf

```

For more advanced automation of evince and other apps I draw upon a utility Actiona in Accessories in Ubuntu 16.04.  
I don't know if Ubuntu 18.04 has this utility but Actiona can be compiled easily enough.

For example Actiona could work in concert with x-tile .. or do the same operations such as maximising application windows.
But it can be tricky to setup.

To avoid complicating the task I think you would be better to stick with evince command line.

---

### Post by kerry_s on 2018-05-29
this extension still works & it's simple if it does break should be fixable.
[https://extensions.gnome.org/extension/1193/maximized-by-default/](https://extensions.gnome.org/extension/1193/maximized-by-default/)

---

### Post by tellapu on 2018-05-30
@[**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878") Thank you for the **evince command line** tip. This sounds interesting. I have no experience with writing a bash script or python script. What would I need to write in the script in order to have evince open ALL files in a maximized window?
 [B]
@[**[COLOR=#000000]kerry_s[/COLOR]**]("https://ubuntuforums.org/member.php?u=132335") [/B]Thank you for tip regarding the **[Gnome extension ]("https://extensions.gnome.org/extension/1193/maximized-by-default/")Maximized by Default.** It works well on my system. A logic side-effect is that EVERY window is maximized (except from [the pop-up window from panel indicator qbirthday]("https://ubuntuforums.org/showthread.php?t=2391594"), I hoped it would also fix ;-) ). This means that even usual desktop windows (e.g. the system or an application asking a question) and launchers (like Synapse, Albert) are maximised. Maybe this extension can be tweaked to only open application windows maximised and/or include a whitelist for windows that won't need to be maximised. I will post a "bug/feature request" on the [extension's github-page]("https://github.com/aXe1/gnome-shell-extension-maximized-by-default/issues").

---

### Post by kerry_s on 2018-05-30
lol, 
> How to have all application windows maximized upon opening? 

can't say it's not all.

---

### Post by tellapu on 2018-05-30
:oops: :) Well, you are write all application windows could mean all windows ;-). But I guess you understood that I meant all "normal" main app windows and not the all the dialog windows :KS.  Do you think it would be possible to tweak the extension in this direction?

---

### Post by kerry_s on 2018-05-30
i'm sure it is, do you know java script? 

the code looks simple. it's just this.
extension.js located at ~/.local/share/gnome-shell/extensions/gnome-shell-extension-maximized-by-default@axe1.github.com
```

const Meta = imports.gi.Meta;

let _windowCreatedId;

function enable() {
    _windowCreatedId = global.display.connect('window-created', (d, win) =>
        win.maximize(Meta.MaximizeFlags.HORIZONTAL | Meta.MaximizeFlags.VERTICAL)
    );
}

function disable() {
    global.display.disconnect(_windowCreatedId);
}

```

---

### Post by tellapu on 2018-05-30
This looks simple but unfortunately I don't know any javascript :(. Can you help?

---

### Post by kerry_s on 2018-05-30
not sure, i had memory loss not to long ago, lost 40 years been trying to relearn, but i have poor retention, i have to read over & over till it sticks.

maybe someone else can help? i'll try & look into it, but it'll take time, maybe a couple days.

---

### Post by tellapu on 2018-05-30
Thanks, any help is welcome!
I am sorry to hear about the memory loss! Hopefully the relearning will get easier over time!

---

### Post by dragonfly41 on 2018-05-30
> [COLOR=#000000]What would I need to write in the script in order to have evince open ALL files in a maximized window?[/COLOR]
Just to avoid wasted time ...
Do you mean all *.pdf files in a given single directory? 
Or do you mean all *.pdf files scattered throughout your file system?

---

### Post by tellapu on 2018-05-30
> **dragonfly41 said:**
> Just to avoid wasted time ...
Do you mean all *.pdf files in a given single directory? 
Or do you mean all *.pdf files scattered throughout your file system?

Thank you, dragonfly41, for your question. It would be great evince would open ALL pdf-files (not just from one directory) but all *.pdf files scattered throughout the file system (including (temporary) files attached to an email). 
Cheers!

---

### Post by dragonfly41 on 2018-06-01
> It would be great evince would open ALL pdf-files (not just from one directory) but all *.pdf files scattered throughout the file system (including (temporary) files attached to an email). 

At first thought this scenario seems straight forward. But it is not.  The workflow set out below departs from the thread title but answers the question about viewing ALL *.pdf files.

I pursued and documented this workflow to the end (took some time) since a searchable bucket of *.pdf files would be useful for my own workflow. Here is a summary of what I did.

(1) The first obstacle I found is that Thunderbird *.pdf attachments cannot be searched through the command line. I found that attachments are embedded in Thunderbird mime formatting. 
[https://support.mozilla.org/en-US/questions/1067402](https://support.mozilla.org/en-US/questions/1067402)
In order to index all Thunderbird *.pdf attachments they have to be saved into a conventional folder or folders in Ubuntu filesystem. This can be done using Thunderbird message filters.

(2) First create a series of folders in /home/user/ directory to hold saved attachments.  You might create a root folder named thunderbird in home directory and in there create subfolders for each of your email accounts.
~/thunderbird/email_account1    (or use the name of your email account)
~/thunderbird/email_account2
~/thunderbird/email_account3

In fact I have eight email accounts but you might have fewer.

(3) We will be using message filters to scan through email account folder to save attachments.  However this option &#8220;Save Attachments&#8221; is not found in the Thunderbird default filters. To enhance message filtering rules we will install an add-on FiltaQuilla .

Download from here ...

[http://mesquilla.com/extensions/filtaquilla/](http://mesquilla.com/extensions/filtaquilla/)

In Thunderbird go to Tools > Addons
In the window select gear icon .. Tools for all add-ons
Install Add-on From File
Navigate to location where FiltaQuilla is downloaded.

e.g. ~/Downloads/filtaquilla-1.3.2-tb+sm.xpi

Install now and Restart Thunderbird.

(4) Now we must set preferences in FiltaQuilla which can extend message filters.
Go to Tools > Add-ons and in the panel showing installed add-ons select FiltaQuilla preferences.
Under Filter Actions tick the box .. &#8220;Save Attachments To&#8221; and then Close.   There are many more advanced options you can choose in FiltaQuila (including regex) but this is sufficient for this particular workflow to save attachments.

(5) The next option is to setup a custom tag to identify attachments to be saved.  The reason for this extra step is that in message filters it is difficult to setup specific matching rules and so the safest option is to explicitly tag email messages which will save their attachments.  To setup a custom tag go to top bar, Message > Tag > New Tag and define this new custom tag as Save, choosing an appropriate colour.  Now when any message is received with an attachment the tag Save can be attached to make it easier for message filters to Save Attachment for future viewing from the designated folder. Untagged attachments will not be saved.

(6) After creating the folders for saving *.pdf attachments now open Thunderbird and go to Tools > Message Filters (or, same effect, open main Thunderbird GUI click on Advanced Features > Manager message filters).   For each email account add this filter:-

Filter name: Save attachments to folder
Apply filter when:
tick - Manually Run
tick - Getting New Mail

tick - Match all of the following
and then add Rule in filter
[Tags]            [is]          [Save]

Perform these actions:
Save Attachments to:   /path/to/your/folder/
                                         e.g.    ~/thunderbird/email_account1/  
                                         (or choose to use account name ~/thunderbird/joe@example.com/)
                                                             
 Click O.K. to save message filter. 
 Ensure that filter is enabled.
 Click on &#8220;Run Now&#8221; and view Filter Log to test that filter is working.
 
 (7) Repeat to create similar message filters for each of your email accounts/folders. Remember to tag all message attachments which are to be saved with Save tag.
 
 (8) Now in Thunderbird navigate to each email account, ensure that messages to be saved are tagged &#8220;Save&#8221;, go to top bar Tools > Run Filters on Folder, and your tagged attachments will be saved to the designated folder for that email account.  The log for each run can be inspected.

 ================================================================
 
 (9) At this point we have all files to be viewed in Document Viewer saved in Ubuntu filesystem as conventional searchable files.  Now we progress further.
 
 (10) One command considered for searching through the entire file system is &#8220;locate&#8221;.  This requires the files to be indexed first by using command &#8220;updatedb&#8221;. Now to apply updatedb to the entire filesystem can take minutes so we can exploit the command options to only index specific folders and so speed up the operation. However this option is parked for now and we will use installed packages as below.
 
 (11) We can also use existing packages such as Nautilus or Thunar to explore all *.pdf files to be viewed in your chosen PDF viewer.

Launch Nautilus
Click on search icon.
Click on Computer in left navigator pane to see the entire filesystem
Type pattern &#8220;.pdf&#8221; into search field

Note that some file paths might include this pattern &#8220;.pdf&#8221; but not end with .pdf as file type.
To refine the search click on the + icon at top right ... &#8220;add a new criterion to this search&#8221;
and choose ..

File Type > PDF Postscript

Click on All Files button.

and now you have in Nautilus ALL pdf files throughout your filesystem (including pdf attachments saved from Thunderbird using message filters).

(12) Now in Nautilus you can select either a single *.pdf file or multiple *.pdf files by holding down Ctrl+Alt then clicking on the multiple files to highlight the selection. Next right click on the highlighted files and select from context menu Open With > Document Viewer (evince) or you can open with an alternative PDF viewer.  I see mixed results as discussed below.   In particular evince seems to open a new instance (window) for each selected *.pdf file and the preference might be to show these documents in tabs in one window.

(13)  We try below some other PDF viewers.

(14) Master PDF Editor is found here [http://code-industry.net](http://code-industry.net) and opens pdf documents in tabs.

(15) Okular also opens multiple pdf files in tabs.

(16) Foxit Reader

[https://www.foxitsoftware.com/](https://www.foxitsoftware.com/)

In Foxit reader documentation there is reference to setting/disabling multiple instances here.

[https://www.foxitsoftware.com/blog/how-to-compare-two-pdf-documents-side-by-side/](https://www.foxitsoftware.com/blog/how-to-compare-two-pdf-documents-side-by-side/)

But I can find no such setting in my Linux installation of Foxit Reader. Version 2.4.1.0609.
Perhaps some preferences are missing in the (free) Linux version.

(17) Basically for any PDF Viewer to operate in multiple tabs mode the preference &#8220;Allow multiple instances&#8221; must be disabled in the Viewer preferences.


 ================================================================
 
 **Conclusions**
 
 Attachments must be filtered from Thunderbird format into filesystem folders.
 Thunderbird add-on FiltaQuilta makes it easier to apply filters.
 Nautilus can be used to view all pdf documents curated in filesystem.
 Master PDF Editor seems to be a good alternative to Evince.
 
 I now have a corpus of all pdf files in my filesystem.


References re: saving attachments in Thunderbird

[http://forums.mozillazine.org/viewtopic.php?f=39&t=3025426](http://forums.mozillazine.org/viewtopic.php?f=39&t=3025426)

[http://mesquilla.com/extensions/filtaquilla/](http://mesquilla.com/extensions/filtaquilla/)
 
  ================================================================

---

### Post by tellapu on 2018-06-01
@[**[COLOR=#000000]dragonfly41[/COLOR]**]("https://ubuntuforums.org/member.php?u=1261878") Thanks a lot for this extensive research and work! Hopefully it will be helpful for many in the future. I will read through it when I find time, I am just about to leave for a week.

---

### Post by tellapu on 2018-06-26
> **kerry_s said:**
>  maybe someone else can help? i'll try & look into it, but it'll take time, maybe a couple days.

@kerry_s How are you doing? Have you had time to look into the code of the [Gnome extension Maximized by default]("https://extensions.gnome.org/extension/1193/maximized-by-default/") as you wrote it might be possible to tweak it so it maximizes "normal" main app windows but not dialog windows.
 "extension.js located at ~/.local/share/gnome-shell/extensions/gnome-shell-extension-maximized-by-default@axe1.github.com"

---

### Post by kerry_s on 2018-06-26
> **tellapu said:**
> @kerry_s How are you doing? Have you had time to look into the code of the [Gnome extension Maximized by default]("https://extensions.gnome.org/extension/1193/maximized-by-default/") as you wrote it might be possible to tweak it so it maximizes "normal" main app windows but not dialog windows.
 "extension.js located at ~/.local/share/gnome-shell/extensions/gnome-shell-extension-maximized-by-default@axe1.github.com"

sorry, i never did look into it. i haven't been on gnome yet. i was playing with a different distro i spotted. it had my favorite "elementary os + xubuntu" [http://www.enso-os.site/](http://www.enso-os.site/)
i'm currently back on solus budgie, it's the only rolling release worth using to me.

i still think devilspie2 is the way to go for targeted maximized windows/apps. any which way you have to make a list whether it be white or blacklist, with devilspie2 you can save the list & use it on any distro environment, not just gnome.

---

### Post by tellapu on 2018-06-29
Thank you, kerry_s, for the honest response. At the moment I will continue with the [Gnome extension Maximized by default]("https://extensions.gnome.org/extension/1193/maximized-by-default/") and maybe some day someone can tweak it.
The name of the other tool is not really inviting ;-).

---

### Post by kerry_s on 2018-06-29
> The name of the other tool is not really inviting . 

lol, i wonder how they even decided to name it that.

i did a ubuntu 18 minimal install this mourning, which i'm still setting up & bending it to my will. just doing some scripts to make life easier, thought i'd do a little zenity script to make youtube-dl easier to grab vids from youtube, i just wanted copy & paste simplicity.

---

### Post by dragonfly41 on 2018-06-29
Here is another idea.
In my Ubuntu 16.04 under accessories is a tool Actiona.
This allows actions (emulations of user desktop tasks) to be performed such as maximising windows but much more.
It is like autohotkey in Windows.

Launch Actiona and create your first action which uses Window component.
For example you can look for Window titles as your target and then Maximize.
Create actions for each of your Windows to be maximized.
You can test the script.
Save it for example as maxwin.ascr.
To execute the script from command line you run the command
```
actexec maxwin.ascr
```

---

### Post by tellapu on 2018-06-30
> **dragonfly41 said:**
> Here is another idea.
In my Ubuntu 16.04 under accessories is a tool Actiona.
This allows actions (emulations of user desktop tasks) to be performed such as maximising windows but much more.
It is like autohotkey in Windows.


Thank you for this tip. It is still in the Ubuntu 18.04 repository. I will look into this when I have more time which is lacking for some weeks I expect.

---

