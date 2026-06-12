---
title: "Thunderbird suddenly stopped working in Gutsy Gibbon.  How do I troubleshoot?"
date: 2007-09-09
forum: General Help
---

### Post by GeekLove_JavaStyle on 2007-09-09
Hello All,
I am running Gutsy Gibbon (Ubuntu/Gnome) with the latest patches.  I installed Thunderbird through the Add/Remove programs dialog and then downloaded and installed the lightning 0.5 (newest version) plugin.  

I imported my mail last night from my Feisty Fawn machine and everything was great.  I applied this morning's patches and rebooted and now Thunderbird won't work.  

Here's what happens, I start thunderbird and can see my the default welcome screen in the preview pane.  As soon as I load a message, Thunderbird silently exits.   I tried rebooting the machine again, but nothing changed.   

How can I troubleshoot this?  Is there a log somewhere? 

Thanks in Advance,
Steven

---

### Post by ThrobbingBrain66 on 2007-09-09
Open Thunderbird in a terminal.  When it crashes, it'll ouput the error to the terminal.  Just copy and paste the output here.

---

### Post by GeekLove_JavaStyle on 2007-09-10
Thanks for the suggestion.  The error message was:

Segmentation fault (core dumped)


(nothing else, unfortunately)

Also of note, I'm not really having any other major issues.  Firefox, pidgin, and eclipse (which I installed myself) work great, so I assume GTK is working correctly?

---

### Post by fjgaude on 2007-09-10
Try starting it from a terminal as mozilla-thunerbird --verbose to see if more info comes out.

frank

---

### Post by GeekLove_JavaStyle on 2007-09-10
I couldn't find the verbose mode nor mozilla-firefox command.  

steven@x2:~$ thunderbird --help
Usage: /usr/lib/thunderbird/thunderbird-bin [ options ... ] [URL]
       where options include:

X11 options
        --display=DISPLAY               X display to use
        --sync          Make X calls synchronous
        --no-xshm               Don't use X shared memory extension
        --xim-preedit=STYLE
        --xim-status=STYLE
        --g-fatal-warnings              Make all warnings fatal

Mozilla options
        -height <value>         Set height of startup window to <value>.
        -h or -help             Print this message.
        -width <value>          Set width of startup window to <value>.
        -v or -version          Print Thunderbird version.
        -P <profile>            Start with <profile>.
        -ProfileManager         Start with Profile Manager.
        -UILocale <locale>              Start with <locale> resources as UI Locale.
        -contentLocale <locale>         Start with <locale> resources as content Locale.
        -safe-mode              Disables extensions and themes for this session.
  -jsconsole           Open the Error console.
  -addressbook         Open the address book at startup.
  -compose             Compose a mail or news message.
  -mail                Open the mail folder view.
  -options             Open the options dialog.
  -news                Open the news client.


I did notice that in safe-mode, it hasn't yet crashed.  All I have installed is lightning.  All I did was go to the add extensions page from thunderbird, download the file, and install it from local disk.  This was the same procedure I used in Feisty and Windows to install lightning.

Any ideas on how to troubleshoot?

---

### Post by ThrobbingBrain66 on 2007-09-11
The easiest way would be to uninstall the Lightning extension and see if that solves the problem in regular mode.  If it does, you can try downloading the plugin again, either by hand or through the plugin manager and reinstalling it.

---

