---
title: "Keep recieving &quot;Sorry, try again&quot; message when entering password"
date: 2021-10-10
forum: General Help
---

### Post by hwrobo on 2021-10-10
Hello,

I am super new to Ubuntu so first and foremost I apologize if this is confusing. But I am currently taking a coding bootcamp and we have just begun using Ubuntu. Currently, we are trying to use sudo, but everytime I am asked to enter my password I recieve the "Sorry, try again" message. I am doing this on a remote server, just my Windows 10 laptop, and don't remember even being asked to create a password when I installed the terminal. I tried to reset it in recovery mode, but that hasn't seemed to work either and now I have no idea what course of action to take. Any help would be appreciated!

---

### Post by grahammechanical on 2021-10-10
Did you actually install Ubuntu as a dual boot with Windows 10? Or, did you install in Windows 10 the Windows Subsystem for Linux (WSL)? 

[https://docs.microsoft.com/en-us/windows/wsl/install](https://docs.microsoft.com/en-us/windows/wsl/install)

A Ubuntu install to a hard disk would require us to choose a username and password. Does Windows 10 require you to have a username and password? You say you do not remember being asked to create a password when you installed the terminal? Ubuntu comes with a terminal by default. We do not need to install one. In fact in Ubuntu we cannot install software without entering a password.

You situation is confusing to us. Please give more detail of what you did to install Ubuntu.

Regards

---

### Post by Impavidus on 2021-10-11
I understand you're doing this on a remote Ubuntu server, from a Windows 10 client. The password you need is your password on the server. It has nothing to do with anything you did to your Windows 10 client. Have you installed the server yourself? Then it's the password you gave when installing the server. If not, ask the admin who created a login for you on the server.

---

