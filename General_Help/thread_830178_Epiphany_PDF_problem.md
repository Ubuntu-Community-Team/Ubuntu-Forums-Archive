---
title: "Epiphany PDF problem"
date: 2008-06-15
forum: General Help
---

### Post by dbbolton on 2008-06-15
I installed Adobe Acrobat Reader, but then removed it later. Now when I try to access a PDF file from Epiphany (like to download it) I get this error:

> 
Could not launch Adobe Reader 8.1.2. Please make sure it exists in PATH variable in the environment. If the problem persists, please reinstall the application.
Is there a way to get Epiphany to treat PDF files like other files, that is, to bring of the Download dialogue box, or maybe to open them with Evince instead?

---

### Post by BlackShift on 2008-06-30
I had the same problem with firefox with a new installation of ubuntu (8.04) when I kept using my .mozilla from 7.10. It even crashed my browser right after that exact same message, so it was kinda hard to track down with only 1 second to read the error.

I think I've fixed it by removing 
```
~/.mozilla/plugins/nppdf.so
```
and then also the pluginreg.dat (substitute your own profile dir)
```
~/.mozilla/firefox/8xr92i2u.default/pluginreg.dat
```

I do not know whether epiphany does something similar, if it does, this might help.

---

### Post by feistybird on 2008-10-30
> **dbbolton said:**
> I installed Adobe Acrobat Reader, but then removed it later. Now when I try to access a PDF file from Epiphany (like to download it) I get this error:

Is there a way to get Epiphany to treat PDF files like other files, that is, to bring of the Download dialogue box, or maybe to open them with Evince instead?

install mozplugger  (sudo apt-get install mozplugger)

Then it should automatically handle all your pdf file., if it can't find acroread plugin, it will then try evince, and kdpf, and then xpdf at the last.

If you have multiple pdf viewer installed, and want to choose a default pdf viewer for your epiphany-browser, you can edit the mozpluggerrc by :

sudo gedit /etc/mozpluggerrc


search for "pdf", then move your preferred viewer's line to the first line of this section, you can also add a line to open the PDF by any other  viewers you want to use, for example, I use "wine foxit pdf reader":

========
```
application/pdf:pdf:PDF file
application/x-pdf:pdf:PDF file
text/pdf:pdf:PDF file
text/x-pdf:pdf:PDF file
```
[color=#FF0000]	repeat noisy swallow(wine-foxit) fill: wine-foxit "$file"[/color]
repeat swallow(acroread) fill: acroread7 -openInNewWindow "$file"
	repeat swallow(documentShell) fill: acroread5 -geometry +9000+9000 +useFrontEndProgram "$file"
[color=#000099]	#repeat noisy swallow(evince) fill: evince "$file"[/color]
	#repeat noisy swallow(kpdf) fill: kpdf "$file"
	#repeat noisy swallow(Xpdf) fill: xpdf -g +9000+9000 "$file"
	GV()

In you case, You can simply cut the "evince" line, and paste it to the first row of the section.

---

### Post by TaoTe Traven on 2011-11-21
I have the same problem, pdf is downloaded and opend in the browser, but the window of the browser stays blank or freezes. Sometimes toggling the statusbar state (in View-tab) makes the embedded acroread and thereby the downloaded pdf visible.

This not showing of pdf's is a show stopper if you try to access files from webpages that start the download via some jave script. In these cases you do not have the option to use 'save link', because that only saves rubbish. Currently I start Firefox in such cases, but that is a pitty...

**How can I recreate the default behaviour of Epiphany to open pdf in an external evince window?** This is most reliable and perfectly useful. Actually I do not understand what opening pdf's inside a Browser is good for. I think it is done solely because it is possible...

The files in ~/.mozilla/ mentioned in an earlier post I have not found, and also the mozplugger did not solve the problem, at leat not with my Ubuntu 10.04 (lucid), kernel 2.6.32-35-generic, Gnome 2.30.2. There exists a workaround by removing some acroreader related system files; this actually recreates the default behaviour of Epiphany. However, some ugly update or background tool - no clue what exactly - persistently restors the deleted files. I do not want to write a script that automatically deletes these files every time I reboot, this seems too dirty a hack to me...

Thanks, and I hope to see an option to select Epiphany's default behaviour in the Edit/Preferences settings soon. Currently I use Epiphany 2.30.2 and am very happy with the performance, wouldn't there be this PDF problem.

---

