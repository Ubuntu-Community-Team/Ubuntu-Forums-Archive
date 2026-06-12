---
title: "Sharing applications between Windows 10 and Ubuntu"
date: 2018-09-14
forum: General Help
---

### Post by jbcohen on 2018-09-14
How do I use a Windows 10 software package on my Windows 10 laptop while on my Ubuntu laptop.

---

### Post by wildmanne39 on 2018-09-14
The short answer is you don't. You can run some applications in wine but results vary greatly or you can install virtualbox in ubuntu and then install windows in it and that will allow you to boot windows inside of ubuntu without rebooting into windows, it will be in what is called a virtual environment.

This may require another license for windows.

I recommend if you need window applications then dual boot windows and ubuntu and boot into windows as needed.

You may also find linux applications that are comparable to the windows applications that you need.

[https://www.virtualbox.org/](https://www.virtualbox.org/)

---

### Post by Holger_Gehrke on 2018-09-14
@wildmanne39: I think he means remote control of a PC running Windows from a PC running Ubuntu ...

Set your Windows machine up to allow remote desktop connections and install a client for RDP (remote desktop protocol) on the Linux machine. Since I've been free of Windows since Windows 7 I can't help you with the Windows side of this and there's lots of choice (and lots of tutorials on the net for each of those choices) on the Linux side.

Holger

---

### Post by HermanAB on 2018-09-14
Windows 10 now includes SSH support, so you can use that too.

---

### Post by dragonfly41 on 2018-09-14
It is some months since I played with Windows 10 (I have dual boot) but I played with Windows Subsystem for Linux (WSL)
which is a native version of Ubuntu running *inside* Windows 10.

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

I don't know if it is feasible for your Ubuntu laptop to communicate through that.

---

