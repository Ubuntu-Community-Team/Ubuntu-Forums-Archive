---
title: "Difference between Terminal and a Terminal emulator ?"
date: 2015-08-08
forum: General Help
---

### Post by ahmed15 on 2015-08-08
I know that a shell is what actually handles the commands and send it to the operating system to execute.

However, I am not sure if i understand the difference between the terminal and terminal emulator.

All i understand that a terminal is historically a physical device but what we deal now is the emulator which is a program that gives you access to the shell ?

It that true ? or what is the actual difference between the two ?

---

### Post by SeijiSensei on 2015-08-08
Yes, some of us are old enough to remember typing into a terminal device that was connected directly to the computer, usually over a serial cable or modem.  My first such device was a [Teletype Model 33]("http://www.bytecollector.com/images/asr-33_vcf_02.jpg").  It had the ability to store programs and data on paper tape! You can see the tape device to the left of the keyboard in the linked picture. 

Linux can still handle these types of connections using the "getty" program that comes with Ubuntu by default.  However most shell communication these days is handled over the Internet using SSH.

---

### Post by NM5TF on 2015-08-08
"Off the top of my head, a terminal is the end of a line. So, back in the day when the computer was a mainframe serving many user accounts, what you'd be sitting at with your keyboard and display would be a terminal.

A terminal emulator is when you're using a computer (a turing machine) to provide the function of a terminal in software. This usage would typically come up because the computer would be 'imitating' a particular type of terminal in order to communicate with the mainframe.

A very popular terminal is/was the VT100. So if I telnet right now to the server of the local freenet (if they still exist) I'd be using VT100 emulation.

http://en.wikipedia.org/wiki/Vt100"

basically a "terminal" is a physical device......a "terminal emulator" is some software that emulates (imitates) that device.....

---

