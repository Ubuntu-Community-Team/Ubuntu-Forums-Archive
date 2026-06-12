---
title: "Restore everything after every reboot and lock out"
date: 2024-06-20
forum: General Help
---

### Post by 13stokes31 on 2024-06-20
Hello,

I would like to use Ubuntu in my school. But I have a couple of questions about how to make certain configurations.

I have seen in Windows a program that allows you to reset the user account every time the computer is restarted. The program in Windows is called "Deep Freeze". It would be nice if there was an option that allows this for the education part.

On the other hand and related to the above, would it be possible to block the change of settings, wallpaper?

---

### Post by TheFu on 2024-06-20
I'm always amazed when people assume that something possible on Unix systems since 1970 isn't possible?

If you want the user's HOME directory to be reset at every logout/login, you can trivially script that assuming they have bash as the default shell and you can script just a tiny bit and understand Unix file/directory permissions.  There is no requirement under Unix for the logged in user to have write access to their own HOME directory, for example.

Remember, by default, users cannot modify system files on any Linux (well, there are a few exceptions, but nobody should be running those distros).

Or you could look into using a Guest Account?  While this has been deprecated for security reasons, you can find instructions to allow it under Ubuntu.  Guest accounts can introduce security issues that wouldn't be obvious, if it you do go this method, be careful.

OTOH, a kiosk mode for Linux is well traveled and there are lots of how-to guides to accomplish it.  If what you want is a kiosk, I wouldn't start with Ubuntu.  I'd start with TinyCore.

---

### Post by grahammechanical on 2024-06-20
When we install Ubuntu we are asked for a user name and a password. Whenever that first user logs in he/she will work as a standard user and be very limited as to what can be modified. When a standard user tries to modify something important he/she will be asked to authenticate the action. Only the first installed user can do that by entering the password.

The first installed user can add other users and they will run as a standard user unless the first user gives them administrator privileges (first user password needed).

So, only you can log in as your username and password (if kept secure). Other users will be forced to log in under their user names and password but will not be able to modify anything important unless you have granted them to have administrator privileges. You would not do that would you?

Every so often you might want to do some house-keeping by using your administrator role to delete all additional users. That will remove all files created. You can then add new users and things can start all over again.

Or, you might want to investigate Edubuntu. It may have already solved your problem.

[https://www.edubuntu.org/](https://www.edubuntu.org/)

[https://discourse.ubuntu.com/t/edubuntu-24-04-lts-released/44455/1](https://discourse.ubuntu.com/t/edubuntu-24-04-lts-released/44455/1)

Regards

---

