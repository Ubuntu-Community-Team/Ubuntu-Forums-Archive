---
title: "Start vmware virtual machine with a gnome launcher."
date: 2006-07-04
forum: General Help
---

### Post by edgardz on 2006-07-04
Hi,

Sorry.. this is so simple... but I just don't find the way to start my Windows-XP-vmware with a shortcut on my gnome desktop ? Anyone... can tell me ?

Edgardz

---

### Post by scxtt on 2006-07-04
give this a try:

create a file named vmware.desktop in ~/Desktop

put this inside that file:
[indent][Desktop Entry]
Encoding=UTF-8
Name=VMware Server Console
Comment=Run and manage virtual machines
Exec=vmware
Terminal=false
Type=Application
[color=red]Icon=vmware-server.png[/color]
StartupNotify=true
Categories=Application;System;
X-Desktop-File-Install-Version=0.10
MimeType=application/x-vmware-vm;[/indent][color=red]NOTE[/color] you may need to supply the full path to the icon file ...

---

### Post by edgardz on 2006-07-04
Thanks for the reply... but i want to directly start my .vmw files .. any tips ?

---

### Post by givré on 2006-07-04
I think it's impossible, you can't pass command inside the virtual machine, yeah that's could be great, but i don't think it's possible for the moment. But why you need your XP to watch wmv? Does they have DRM? the only things you couldn't watch in linux are DRM files.

---

### Post by edgardz on 2006-07-04
He he ... sorry for the error.... I mean .. directly launch my .vmx files (virtual machine)...

---

### Post by givré on 2006-07-04
ok sorry :cool: 
So to do that, you just have to change your exec line, like that:
```
Exec=vmware /path/to/your/vmx/file.vmx
```
And that's should be okay

---

### Post by edgardz on 2006-07-04
ye... I know... this is the first think I tried.... but it doesn't work... but i find the prob... this is stupid... i have space in my path...

.../vmware/Windows XP/...

Shame on me...

---

### Post by givré on 2006-07-04
use backspace to use special caracter, but you probably already know that

---

### Post by mod187 on 2006-08-15
> Exec=vmware /var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx


Well, he may know that, but, unfortunately, I don't.

What would I use in place of the space?
'~'? I tried that, and it didn't work.

Above is my exec line

---

### Post by givré on 2006-08-15
```
Exec=vmware /var/lib/vmware/Virtual Machines/Windows XP Professional/Windows XP Professional.vmx
```
should be
```
Exec=vmware /var/lib/vmware/Virtual\ Machines/Windows\ XP\ Professional/Windows\ XP\ Professional.vmx
```
:cool:

---

### Post by mod187 on 2006-08-15
Many thanks... works like a charm!

---

### Post by lorre on 2006-08-16
Is it possible to bypass the "connect to" select screen? I want to go immediately to my vm by typing: vmware -x /path/to/image but I still get the "connect screen" where I have to select localhost and press 'ok'. Can't I give this setting as a commandline parameter or in the vm configuration?

---

### Post by Ron Cook on 2006-09-03
> **lorre said:**
> Is it possible to bypass the "connect to" select screen? I want to go immediately to my vm by typing: vmware -x /path/to/image but I still get the "connect screen" where I have to select localhost and press 'ok'. Can't I give this setting as a commandline parameter or in the vm configuration?

Yes, it is possible.

If you include -l along with the -x, activating the desktop launcher will start the virtual machine image, and connect to localhost.

The relevant line in my vmware.desktop file (formatting from earlier in this thread) is:


( -l is lowercase L )

```
Exec=vmware -l -x /var/lib/vmware/Virtual\ Machines/Windows\ 2000\ Professional/Windows\ 2000\ Professional.vmx
```

---

### Post by lorre on 2006-09-03
@ron, thnx! I was still looking for this.

---

