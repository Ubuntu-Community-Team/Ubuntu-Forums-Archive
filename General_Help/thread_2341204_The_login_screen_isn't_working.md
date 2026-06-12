---
title: "The login screen isn't working"
date: 2016-10-25
forum: General Help
---

### Post by billiarddaddy on 2016-10-25
History:
I updated to a development build 16.10 LTS and this afternoon updated to 16.10, non-development build.

Everything comes up fine when booting.

When I enter my password and strike ENTER, it thinks for a minute, my monitor flashes like I lost a video feed and then I see my login screen again waiting for my password.

:confused::confused::confused:

I've tried this with both Ubuntu and Gnome desktop and I get the same results. When I select Unity desktop it just sits there thinking after I type in my password and strike ENTER. Nothing else happens.

I'm certain I've broken something quite well although I have no idea what or where to begin.

For the moment I'm using a live Kubuntu on my system so I have access to the file structure.

Any help is greatly appreciated. Thank you.

---

### Post by ajgreeny on 2016-10-26
Try logging in to a tty command line; at the login screen use Ctrl+Alt+F1, enter you username, then password when asked (which will not show on screen) and once logged in run command ```
ls -la | less
``` which will allow you to scroll in command line if there is too much output using the page-up/down or cursor keys.

Look to see if there is any incorrect ownership of files or folders; everything except probably the second line should show your username but that second line should look like **drwxr-xr-x   4 root   root   4.0K Apr 26  2015 ../**
If you see that **root root** showing in any other lines your problem may be incorrect ownership of files or folders, and might be solved by running command ```
sudo chown -R username:username /home/username
```using your username rather than the word username, of course.

Have you ever used **sudo** for a GUI application in order to give it root permissions, as that can change ownership of files or folders in your home?

---

### Post by billiarddaddy on 2016-10-26
Thanks. I'll give this a shot.

 > Have you ever used **sudo** for a GUI application in order to give it root permissions, as that can change ownership of files or folders in your home?

Not that I recall immediately but I suppose it's possible. The most recent application I installed was Android Studio and I think it did require sudo when launching an .sh file to run the application but I don't think that would affect my /home/ do you?

---

### Post by billiarddaddy on 2016-10-26
> ls -la | less

So there were a few folders that belonged to root:root - at the top of the list was ~

I ran your recommended command but still no change in results.

Since I'm getting different symptoms depending on which desktop environment I'm using, would that point to reinstalling Gnome or Ubuntu desktop applications?

Or is there something else that they are all sitting on that needs to be addressed?

Thanks again.

---

### Post by ajgreeny on 2016-10-27
What were those folders that belonged to root?
Were you able to login as your user from the command line as I suggested; I presume you must have been able to do so in order to run that chown command, but I just want to check.
Did the chown command show any errors, or did it run and go back to the command prompt?

---

