---
title: "Need help opening .pde files with Processing language"
date: 2015-08-09
forum: General Help
---

### Post by boxcorner on 2015-08-09
Hello

This request for help concerns using a programming language called Processing 2.2.1 with Ubuntu 12.04 LTS

[https://processing.org/](https://processing.org/)

I have installed, and am using, the Processing language with Ubuntu.
I have created a starter on my desktop, which enables me to start the Processing Development Environment (PDE).

Processing stores code in files that have a .pde extension.
I can open .pde code files from the PDE without any difficulty.

However, when I right-click on on a .pde file > *Open With* > *Other Application*, Processing is not listed.
Similarly, when I right-click on on a .pde file > *Open With* > *Other Application* > *Show Other Applications, *Processing is still not listed. 

Could someone please tell me how to get Ubuntu to recognise 'Processing' as an application which appears in the list, when I right-click on a .pde file?

---

### Post by ajgreeny on 2015-08-09
Use the option of "Custom command" instead of a specific program for the new application and then use whatever the command is that is used to start Processing Development Environment and will presumably the same as you used for the desktop launcher.

---

### Post by boxcorner on 2015-08-11
Thanks for your reply.

Whereabouts is  the option "Custom command"located?  Perhaps this sounds foolish, but I can't see it :~/

---

### Post by howefield on 2015-08-11
Try adding %f to the end of the exec line in your launcher, so the line looks like:

Exec=pde %f

(I am guessing at the name of the application in the line, it may not be pde). You should now see your application in "Open with > other applications list.

If you don't then it is easy enough to reverse the above.

---

### Post by boxcorner on 2015-08-11
Thanks for your suggestion.
If you mean : Modify this starter > Basic tab then add %F at the end of the line in the Command: field
then that didn't work, so I've reversed it. 
BTW - I didn't re-boot after adding the %F, should I have?

---

### Post by ajgreeny on 2015-08-11
I use thunar as file manager in Xubuntu and in that the "Custom command" option is in the "Use other application" dialogue window; regrettably I don't know if that option is available in nautilus, the ubuntu file manager, but if it is I can not find it in my VirtualBox VM of Ubuntu.

A reboot is not needed after an edit of the launcher that you have; just save the file and that should do it.

---

### Post by boxcorner on 2015-08-12
Thanks for trying to help.

Addendum
======

I found this :[ http://askubuntu.com/questions/396857/how-can-i-add-processing-to-the-unity-launcher]("http://askubuntu.com/questions/396857/how-can-i-add-processing-to-the-unity-launcher")

I tried what is suggested under : *Associate .pde files with Processing* but it doesn't work with my Ubuntu configuration.

---

