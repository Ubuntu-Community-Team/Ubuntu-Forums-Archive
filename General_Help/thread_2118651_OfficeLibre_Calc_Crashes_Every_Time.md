---
title: "OfficeLibre Calc Crashes Every Time"
date: 2013-02-21
forum: General Help
---

### Post by SpikeLS6 on 2013-02-21
When I open OfficeLibreCalc, it begins to load, but crashes within seconds, disappearing from the display. If it does come up again, I always have to go through the restoration process, which it usually completes, and I get a new, blank spreadsheet. However, when I try to bring up a file, it nearly immediately crashes again and disappears from the display.

Would this be a Unbuntu problem (just upgraded to 12-10 a week ago), or should I query the LibreOffice site? Is there a repair code or tool that could be used in Terminal?

Spike

---

### Post by Impavidus on 2013-02-22
You could try starting libreoffice from a terminal. It may give you a useful error message.

---

### Post by SpikeLS6 on 2013-02-25
Ran a launch for Calc in Terminal and got the following errors:

michael@michael-desktop-E:~$ libreoffice --calc
javaldx: Could not find a Java Runtime Environment! 
Please ensure that a JVM and the package libreoffice-java-common
is installed.
If it is already installed then try removing ~/.libreoffice/3/user/config/javasettings_Linux_*.xml
Warning: failed to read path from javaldx
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 13: Having multiple <family> in <alias> isn't supported and may not works as expected

Notice that it did not finish to the command line.

I installed the "libreoffice-java-common" file from the Software Center. Same result.

I tried to "rm" the second suggested file, but could not identify it with "find" to remove it.

Can anyone suggest anything else to try? I am running Calc 3.6.2.2 from the Update to 12-10.

Spike

---

### Post by HermanAB on 2013-02-25
Simple. Don't use Calc. Gnumeric is much better.

---

### Post by SpikeLS6 on 2013-02-25
I installed and tried Gnumeric quickly. It will open the troublesome file with no problem, and I can even make changes in it and save the new file.

I will hang on to this program in place of LibreOffice for the time being. 

Thank you for the suggestion.

Spike

---

### Post by Impavidus on 2013-02-25
That java warning is quite standard and shouldn't harm. It just means you won't have some functionality that you won't miss. The fontconfig warning may be more important. But then, did you say you didn't get the prompt back? That would mean the program still runs, but doesn't open a window.

Besides, in your second post you again mentioned your e-mail address. I already asked the mods to remove it from your first post.

---

### Post by SpikeLS6 on 2013-02-25
I see a few things I would like to change in Gnumeric, but over time I can learn them from the Help file.

On the Terminal, I am thinking every command should lead back to the command line. When I tried to open Calc, I never saw another command line unless I cancelled the screen and restarted a new one. Terminal simply stalled after the first couple of errors. I sent error messages, probably to LaunchPad, so perhaps they may come up with a fix on one of the next Updates.

I will refrain from posting my email address; wrong forum. Thank you for the heads up.

Spike

---

