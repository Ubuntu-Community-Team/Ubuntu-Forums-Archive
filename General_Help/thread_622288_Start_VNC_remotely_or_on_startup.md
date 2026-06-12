---
title: "Start VNC remotely or on startup"
date: 2007-11-24
forum: General Help
---

### Post by scottnadeau on 2007-11-24
Hi all,
I need to be able to start the VNC server service from command line - whenever I reboot remotely it does not start up...I am able to connect from the command line but not via VNC.  I'm sure this is something simple, but I'm not very Linux savvy.

For now, I wait until I can get to the machine and turn on 'allow others to control my desktop' from the remote control GUI.

Thanks for any help...
Scott

---

### Post by scottnadeau on 2007-11-24
Hmm...it just occurred to me that since no user is logged in at the console, there is no desktop to control.  I'm I barking up the right tree?  If so, how do I solve it?  Is there a way to launch a GUI session from the command line?

---

### Post by bthoward on 2007-11-25
On my Mythbuntu box (which auto logs into an X session and launches the frontend) I simply log into the console and run this:
x11vnc -forever -usepw -httpdir /usr/share/vnc-java -httpport 5800
That lets me connect via the web client or the vncviewer console client or via various windows clients.  Then when I'm done I dump that process and log out.  

That way I can have VNC but I don't have to leave it running all the time.  One extra layer of protection.

---

### Post by scottnadeau on 2007-11-25
Hi bthoward - thanks for that.  May I ask how you are auto logging into an X session and launching the front end on startup?  Does that include entering a username and password at the initial X login screen?

Thanks!
Scott

---

### Post by krunge on 2007-11-26
> **scottnadeau said:**
> Hi bthoward - thanks for that.  May I ask how you are auto logging into an X session and launching the front end on startup?  Does that include entering a username and password at the initial X login screen?

Thanks!
Scott

Have a look at these links:  [http://www.karlrunge.com/x11vnc/#faq-service]("http://www.karlrunge.com/x11vnc/#faq-service")
[http://www.karlrunge.com/x11vnc/#faq-display-manager]("http://www.karlrunge.com/x11vnc/#faq-display-manager")

---

### Post by jmdeeme on 2008-02-23
When I try to start x11vnc remotely, sometimes it works and most other times it does the below following. Has anyone else seen this and do you know what the problem is so I it can be fixed.  A lot of times I end up having to reboot the server a couple to finally get it to work.  Any help would be greatly appreciated.


sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display:0
[sudo] password for administrator:
23/02/2008 14:47:54 passing arg to libvncserver: -display:0
###############################################################
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  **  WARNING  **  WARNING  **  WARNING  **  WARNING  **   @#
#@                                                           @#
#@        YOU ARE RUNNING X11VNC WITHOUT A PASSWORD!!        @#
#@                                                           @#
#@  This means anyone with network access to this computer   @#
#@  will be able to view and control your desktop.           @#
#@                                                           @#
#@ >>> If you did not mean to do this Press CTRL-C now!! <<< @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
#@                                                           @#
#@  You can create an x11vnc password file by running:       @#
#@                                                           @#
#@       x11vnc -storepasswd password /path/to/passfile      @#
#@  or   x11vnc -storepasswd /path/to/passfile               @#
#@  or   x11vnc -storepasswd                                 @#
#@                                                           @#
#@  (the last one will use ~/.vnc/passwd)                    @#
#@                                                           @#
#@  and then starting x11vnc via:                            @#
#@                                                           @#
#@      x11vnc -rfbauth /path/to/passfile                    @#
#@                                                           @#
#@  an existing ~/.vnc/passwd file from another VNC          @#
#@  application will work fine too.                          @#
#@                                                           @#
#@  You can also use the -passwdfile or -passwd options.     @#
#@  (note -passwd is unsafe if local users are not trusted)  @#
#@                                                           @#
#@  Make sure any -rfbauth and -passwdfile password files    @#
#@  cannot be read by untrusted users.                       @#
#@                                                           @#
#@  Use x11vnc -usepw to automatically use your              @#
#@  ~/.vnc/passwd or ~/.vnc/passwdfile password files.       @#
#@  (and prompt you to create ~/.vnc/passwd if neither       @#
#@  file exists.)  Under -usepw, x11vnc will exit if it      @#
#@  cannot find a password to use.                           @#
#@                                                           @#
#@                                                           @#
#@  Even with a password, the subsequent VNC traffic is      @#
#@  sent in the clear.  Consider tunnelling via ssh(1):      @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/#tunnelling](http://www.karlrunge.com/x11vnc/#tunnelling)            @#
#@                                                           @#
#@  Or using the x11vnc SSL options: -ssl and -stunnel       @#
#@                                                           @#
#@  Please Read the documention for more info about          @#
#@  passwords, security, and encryption.                     @#
#@                                                           @#
#@    [http://www.karlrunge.com/x11vnc/#faq-passwd](http://www.karlrunge.com/x11vnc/#faq-passwd)            @#
#@                                                           @#
#@  To disable this warning use the -nopw option, or put     @#
#@  the setting in your ~/.x11vncrc file.                    @#
#@                                                           @#
#@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@#
###############################################################
23/02/2008 14:47:56 x11vnc version: 0.9.3 lastmod: 2007-09-30

---

### Post by krunge on 2008-02-23
> **jmdeeme said:**
> 
sudo x11vnc -auth /var/lib/gdm/:0.Xauth -display:0
[sudo] password for administrator:
23/02/2008 14:47:54 passing arg to libvncserver: -display:0

For the case you showed it looks like you typed:
```
-display:0
```
instead of
```
-display :0
```
i.e no space before the :0

When do the above I get:
```

23/02/2008 16:11:46 *** unrecognized option(s) ***
23/02/2008 16:11:46     [1]  -display:0
23/02/2008 16:11:46 For a list of options run: x11vnc -opts

```

---

