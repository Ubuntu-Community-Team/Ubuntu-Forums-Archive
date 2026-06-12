---
title: "Another post about scroll wheel not working"
date: 2006-11-10
forum: General Help
---

### Post by Lukich on 2006-11-10
Hello.  I installed Ubuntu last night and have been having a lot of fun with it, but suddenly I discovered that the scroll wheel doesn't work.  

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"

As I started typing this message, I noticed the letter "EKS" doesn't work, so I couldn't type in "EKS"org.conf :)

Do you guys know what this can be?

Thanks a lot,
Luka

---

### Post by Lukich on 2006-11-10
Never mind, figured it out.  I have a KVM installed, after reboot both the scroll whell and the letter X came back.

---

