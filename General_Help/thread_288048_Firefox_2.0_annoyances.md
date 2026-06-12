---
title: "Firefox 2.0 annoyances"
date: 2006-10-29
forum: General Help
---

### Post by speedsix on 2006-10-29
1. By default it *still* opens certain links in new windows, according to the release notes it shouldn't be doing this?? I have to install Tab Mix Plus to stop this.

2. The fonts look horrible, chunky and not as sharp.

3. Session restore is a pain as I run FF with Alltray so just shutdown without closing it down first and every reboot it comes up with the Restore Your Session dialog which then screws up Alltray. Can you turn this off?

4. Preferences>Content>File Types is completely useless. Firstly all media plugins (totem etc.) seem to force the opening of files in the browser regardless of what is set in the File Types section. Secondly, I have set files to perform a certain action when clicked but they don't even show in the File Types box so I can't change them. It just seems completely broken. I don't want any files to open in the browser and I only want plugins to be used for embedded media.

5. Find As You Type doesn't have the 'Highlight' or 'Find Next' button anymore which was really useful.


Any ideas to get round these?

---

### Post by Sethro on 2006-10-29
Yeah I am having alot of problems with Firefox 2.0.

Its full of bugs, so I switched to Opera.

---

### Post by whatintheworldisthat on 2006-10-29
2. I REALLY doubt the font problem is only related to firefox, do you have any other appts with font problems?


Sorry to hear you guys have problems, I love firefox and am having no problems.

---

### Post by tommcd on 2006-10-29
[QUOTE

 Secondly, I have set files to perform a certain action when clicked but they don't even show in the File Types box so I can't change them. It just seems completely broken. I don't want any files to open in the browser and I only want plugins to be used for embedded media.


Any ideas to get round these?[/QUOTE]

How did you do that? I can't seem to figure out how to use Preferences>Content>File Types either.

---

### Post by speedsix on 2006-10-29
Here's a screen grab, I'm pretty sure my fonts looked better in Dapper. This is on a brand new edgy install.

[[IMG]http://img70.imageshack.us/img70/7391/screenshotoo1.th.png[/IMG]](http://img70.imageshack.us/my.php?image=screenshotoo1.png)

> How did you do that? I can't seem to figure out how to use Preferences>Content>File Types either.
When I clicked on a link I ticked the 'always perform this action' box. Usually the list just shows Shockwave and nothing else.

Now I mention it I'm sure it was the same in Dapper. I don't want any files to open in the browser. When I click on a .wmv is automatically downloads, when I click on an .mpg it opens in the browser with the plugin yet neither of these file types show in the File Types list??

Also, the FF 2.0 release notes say to disable the Session Restore alter the **browser.sessionstore.resume_from_crash** setting.. which I don't even have?

---

### Post by Sethro on 2006-10-29
> **speedsix said:**
> Here's a screen grab, I'm pretty sure my fonts looked better in Dapper. This is on a brand new edgy install.

[[IMG]http://img70.imageshack.us/img70/7391/screenshotoo1.th.png[/IMG]](http://img70.imageshack.us/my.php?image=screenshotoo1.png)


When I clicked on a link I ticked the 'always perform this action' box. Usually the list just shows Shockwave and nothing else.

Now I mention it I'm sure it was the same in Dapper. I don't want any files to open in the browser. When I click on a .wmv is automatically downloads, when I click on an .mpg it opens in the browser with the plugin yet neither of these file types show in the File Types list??

Also, the FF 2.0 release notes say to disable the Session Restore alter the **browser.sessionstore.resume_from_crash** setting.. which I don't even have?


Wow which font are you using? And size?

I cant seem to get font to look that good

---

### Post by noynac on 2006-10-29
> **speedsix said:**
> ...5. Find As You Type doesn't have the 'Highlight' or 'Find Next' button anymore which was really useful....


Put the following in your userChrome.css file:

/* Use the old-style QuickFind Bar */
#FindToolbar > * {display:-moz-box}

---

### Post by brianfast on 2006-10-29
I think noynac is right.

---

### Post by Jose Catre-Vandis on 2006-10-29
> **tommcd said:**
> [QUOTE

 Secondly, I have set files to perform a certain action when clicked but they don't even show in the File Types box so I can't change them. It just seems completely broken. I don't want any files to open in the browser and I only want plugins to be used for embedded media.


Any ideas to get round these?

How did you do that? I can't seem to figure out how to use Preferences>Content>File Types either.[/QUOTE]

Type about:config in address bar
Type plugin in search bar
Right click on "browser.download.hide_plugins_without_extensions"
and Toggle to "false"
Edit>Preferences>Content>Manage and you will see all your file types revealed for adjustment

---

### Post by speedsix on 2006-10-29
> 
Type about:config in address bar
Type plugin in search bar
Right click on "browser.download.hide_plugins_without_extensions"
and Toggle to "false"
Edit>Preferences>Content>Manage and you will see all your file types revealed for adjustment
Thanks!

Why on earth this isn't enabled by default:-k 

Can't suss out a way to get it to prompt you with the open/save for a certain file type though.

---

### Post by pete on 2006-10-29
> **speedsix said:**
> 3. Session restore is a pain as I run FF with Alltray so just shutdown without closing it down first and every reboot it comes up with the Restore Your Session dialog which then screws up Alltray. Can you turn this off?

This annoyed the bejesus out of me as well.  Go to about:config, and then find "browser.sessionstore.resume_session_once".  Toggle the value to "false", and you should be all set.

---

### Post by tommcd on 2006-10-30
> **Jose Catre-Vandis said:**
> How did you do that? I can't seem to figure out how to use Preferences>Content>File Types either.

Type about:config in address bar
Type plugin in search bar
Right click on "browser.download.hide_plugins_without_extensions"
and Toggle to "false"
Edit>Preferences>Content>Manage and you will see all your file types revealed for adjustment[/QUOTE]

Thanks for the tip. One question though, if I wanted to change all MPEG videos to mplayer, for example, how would I do that? I currently have the 'use this plugin' box selected, and the plugin is 'vlc multimedia plugin'. If I wanted to select the 'open with this application' box, what mplayer plugin would I browse to to do that?

---

### Post by Zdravko on 2006-10-30
> **whatintheworldisthat said:**
> 2. I REALLY doubt the font problem is only related to firefox, do you have any other appts with font problems?


Sorry to hear you guys have problems, I love firefox and am having no problems.
I have the same problem - here:
[http://ubuntuforums.org/showthread.php?t=288566](http://ubuntuforums.org/showthread.php?t=288566)
It seems that FF cannot render correctly bold or fine fonts.

---

### Post by speedsix on 2006-10-30
This best shows the font problem. The reply text looks ok but the bold and small text underneath look bad.

**EDIT** included Windows FF2.0 for comparison




_**Edgy FF2.0**_
   
[img]http://img221.imageshack.us/img221/1818/screenshotne7.png[/img]


_**Windows FF2.0**_

[img]http://img117.imageshack.us/img117/8196/winkj2.png[/img]

---

### Post by Zdravko on 2006-10-30
But can we change this? It is really sad to look blurred fonts.

---

### Post by bionnaki on 2006-10-30
this worked great for me:

[http://ubuntuforums.org/showpost.php?p=1594174&postcount=118](http://ubuntuforums.org/showpost.php?p=1594174&postcount=118)

---

### Post by adolfotregosa on 2006-10-30
also, e.g. [www.ati.com](www.ati.com) the cascating menus are show behind the flash... how do i fix that ?

---

### Post by bionnaki on 2006-10-30
two annoyances I had and fixed:

to get rid of the go button:

about:config
search for hideGoButton
and change to true

to make the location bar a search bar again:

about:config
search for keyword.URL
and modify to
[http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=](http://www.google.com/search?ie=UTF-8&oe=UTF-8&q=)
enable keyword if it is not enabled

---

### Post by Zdravko on 2006-10-30
> **bionnaki said:**
> this worked great for me:
 
[http://ubuntuforums.org/showpost.php?p=1594174&postcount=118](http://ubuntuforums.org/showpost.php?p=1594174&postcount=118)
Hmm, I am afraid to use this method. I think I need to find a suitable combination of fonts and sizes.

---

### Post by speedsix on 2006-10-30
*deleted*

---

### Post by bionnaki on 2006-10-30
> **Zdravko said:**
> Hmm, I am afraid to use this method. I think I need to find a suitable combination of fonts and sizes.

you can always delete the file if you are not pleased. works just fine for me and the fonts/sizes work across ubuntu (ff included).

---

### Post by speedsix on 2006-10-30
Just found out, System>Preferences>Font and select Sub-pixel smoothing (assuming you're using an lcd) Seems to sort the blury fonts out but it's not perfect. Need to experiment with the other options.

Doesn't explain why it looked fine in 1.5

---

### Post by slugicide on 2006-11-04
Cool.  Now all I gotta do to put Fx back in working order is find out how where the "force new windows to open in new tab" option went.

---

### Post by blacha on 2006-11-04
> **pete said:**
> ... Go to about:config, and then find "browser.sessionstore.resume_session_once"...

there is no browser.sessionstore.* anything on my installation ](*,) 

any ideas ?

---

### Post by uid0 on 2006-11-04
Does anyone notice there's no option to automatically add cookie sites to the block list when you delete cookies?  I kinda liked that feature!

---

### Post by aysiu on 2006-11-04
Am I the only one annoyed by Control-W not closing Firefox when there's only one tab open? Anyone know how to change this behavior?

I know I can Alt-F, Q or Alt-F4, but Control-W is a much more comfortable combination for me.

---

### Post by der_joachim on 2006-11-04
One thing which improved font rendering greatly, was putting the following lines in my xorg.conf:

```

    Option         "UseEdidDpi" "FALSE"
    Option         "DPI" "96 x 96"

```

Put these in your Screen section and you should be fine. This is *Nvidia-only* though.

---

### Post by Turin Turambar on 2006-11-05
I got mine FF fonts easily fixed with a simple solution (it's not a FF issue!):

Go to Preferences / Font Preferences. Click on the Details...
Choose Smoothing Grayscale, Hinting Full.

Here's the picture:

---

### Post by Ramses de Norre on 2006-11-08
> **noynac said:**
> Put the following in your userChrome.css file:

/* Use the old-style QuickFind Bar */
#FindToolbar > * {display:-moz-box}

Thanks a lot! I used this feature so much in 1.5 but it's useless without the find next button.

---

### Post by roddersg on 2007-08-07
I have followed the Manage Content Thread and it does show the extensions without content as  indicated.

But, I have this problem.  When I click on files with a ".php" extension, FF downloads the text instead of executing the code.  Similarly, when i click files with the ".zip" extension, it downloads the file, and displays it as text in another tab.

Is there anyway to fix this?

Thanks,

Rodders

---

### Post by roddersg on 2007-08-07
> **roddersg said:**
> 
But, I have this problem.  When I click on files with a ".php" extension, FF downloads the text instead of executing the code.  Similarly, when i click files with the ".zip" extension, it downloads the file, and displays it as text in another tab.

Is there anyway to fix this?


Couldn't wait for the answer, so with hard searching I managed to fix it using this link: [http://kb.mozillazine.org/Downloads.rdf](http://kb.mozillazine.org/Downloads.rdf)

What you have to do is go to your profiles directory, and delete the downloads.rdf file.  There was another .rdf file I deleted as well (while I was in the mood) and it had to do with extensions, I think.  Close everything, restart Mozilla and that's the problem fixed!

Cheers!

---

