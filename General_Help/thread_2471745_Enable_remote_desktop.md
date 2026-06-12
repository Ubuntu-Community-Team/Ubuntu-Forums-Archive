---
title: "Enable remote desktop"
date: 2022-02-08
forum: General Help
---

### Post by olysmt on 2022-02-08
I need to access the device remotely to manage applications and files. But I do not know how to do it. 
Please tell me, what are the ways to connect?

---

### Post by naxal on 2022-02-08
Hello,

1. You can use SSH, by installing OpenSSH server
2. You can use Team Viewer type platform independent remote desktop applications for over the internet GUI Desktop access
3. You can use xRDP for internal network based direct remote desktop connection.

Thanks.

---

### Post by mIk3_08 on 2022-02-08
> **olysmt said:**
> [B][SIZE=2]I need to access the device remotely to manage applications and files. But I do not know how to do it. 
Please tell me, what are the ways to connect? [/SIZE][/B]

You can use an application for this if you want. There are some application that can help you with this concern and will easily navigate you thru the steps and just follow the instruction for installation then. 
you can try tiger or real. try those application maybe it will help you with your needs. There are some instruction in their website for you to follow. Just read it.Good Luck and Cheers.

---

### Post by slickymaster on 2022-02-08
There's also Remmina, which is a remote desktop client written in GTK+

[https://gitlab.com/Remmina/Remmina/-/wikis/home](https://gitlab.com/Remmina/Remmina/-/wikis/home)

---

### Post by mIk3_08 on 2022-02-09
I also agree with slickymaster. Linux Ubuntu Operating System also have a remina remote desktop application. This is also best for remote desktop control application.
Just explore more over it. This is also one of the most high and very good evaluation as a remote desktop application in Linux. So good luck and cheers.

---

### Post by ActionParsnip on 2022-02-09
What do you mean by "Manage applications"? What exactly do you want to do?
You can mount SFTP from Linux systems and MacOS (and Windows with 3rd party tools) to manage files. You don't need a full desktop to do that. The local file manager can manage remote files without issue

---

### Post by Impavidus on 2022-02-09
You can also manage files and applications (for some definitions of "manage applications") from the command line. No need for any desktop or file manager. You can login over ssh. That's the most robust way.

---

### Post by woodnome on 2022-08-17
Hi

I've just started with Ubuntu last week and have now installed TV for remote access but each time, on the laptop I'm accessing, it's asking to click the "Share" button for remote access.  I've followed the settings but each time it still asks.

Can anyone point out where I'm going wrong ?

Thanks in advance

---

### Post by ActionParsnip on 2022-08-17
You can manage files via SSH. What does "manage applications" mean in this context, please?

---

### Post by TheFu on 2022-08-17
I use ssh, sftp, rsync and ansible to manage remote systems.  Any Linux file manager should support sftp:// access to another Linux system if it is running openssh-server. From MS-Windows, a popular sftp client application is WinSCP, which I've used.  Others use Filezilla in sftp mode, but there was a bug for a few months when filezilla was released a few years ago that prevented sftp from working, so be certain you get a newer version.

I seldom need a remote GUI, but when I do, there are two methods.

a) remote X11.  This is built-into all Unix workstations.  We can run nearly any remote program with a GUI using ssh tunnels and have the "window" for the application displayed on the workstation we are sitting behind.  This is how I work 99% of the time.  Right now, I have windows running on 5 other systems, but being displayed locally.  Thunderbird, firefox, a video editer, gnubiff and a number of terminals are all doing this now. This method avoids the overhead of a full desktop and lets those programs behave and feel like they are running local.  Select/paste works between all the windows using the X-buffer, just as expected. I've been working this way since 1993 - though we didn't have ssh until around 1995.  The typical command to run a remote "cmd" on another system is:
```
$ ssh -X userid@remote  cmd
```
I use xterms. They are lite and fast. To run one on regulus using "thefu" as the username, 
```
$ ssh -X thefu@regulus  xterm -sb &
```

b) x2go.  This is the fastest of the full desktop options that I know.  2-3x faster than RDP or VNC, but there are limitations in the DEs supported.  Those DEs that demand direct access to hardware like Gnome3/Gnome4 or Plasma cannot be used. After all, the remote system doesn't need to have any GPU installed at all.  x2go uses ssh for authentication, so get ssh working between the client and server BEFORE starting.  Follow the instructions on the x2go project website.  For someone who know what they are doing, setting up x2go is about 3 minutes for both the client and server combined.   If the client workstation is MS-Windows, be certain to pull the font package down and install it too.  For Linux clients, the fonts are already installed.  The remote system should have a lite-DE installed - XFCE, LXQt, Mate or no DE at all, then you can use openbox or fvwm or some other pure WM as the startup command.
These days, I only use x2go when I'm traveling.  I've used it from 5 different continents to connect back home. It works and since all the traffic goes through ssh using key-based authentication, it is probably more secure than any other options.


You may have noticed that all of these options are ssh-based, so you'll need to get ssh working between the client and server anyway.  There are a few tools I think every Linux/Unix user should know.  My top 5 list includes ssh, regex (pattern matching), rsync, cron, and 1 good, scripting language (bash, perl, python, ruby, or nawk).  No need to be an expert in any, but not being afraid to use them is required.  With just those 5 items, there is very little that cannot be performed, scheduled, automated to be handled efficiently.

The sad thing is that most books and people will suggest VNC or RDP because they've never tried x2go (or other NX-based remote desktop solutions).  They don't know.  The built-in RDP from the Gnome guys tends to be buggy between different releases and bloated.  If all your systems are running 22.04, it would be worth trying, so you can see what I've said is true.  Don't expect it to work between different releases.

---

