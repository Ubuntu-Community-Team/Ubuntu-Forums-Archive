---
title: "Need help setting up special commands"
date: 2017-10-06
forum: General Help
---

### Post by umbotteswillen on 2017-10-06
This question qill probably require advanced knowledge of bash scripting, so if there is any better place to ask this, please direct me to it.
I need help with setting up a special user that can be accessed from the internet, which can do _nothing_ but execute the following commands:

**start server** - Logs in an administrator user that then starts a java command line application
    
[LIST]
[*]The administrator user is required so that the the person connected via the internet can log out without stopping the server
[*]The command line application shall not be shown to the logged in person, or atleast that person should be prevented from typing any commands the program accepts
[*]If the administrator user is already logged in and the application running, this command should do nothing or warn the user that the application is already running
[/LIST]
 
**stop server** - Sends the "stop" command to the command line application to shut it down properly and logs out the administrator user
    
[LIST]
[*]Needs to be working even if the application was started by a different person beforehand
[*]Should do nothing or warn the user if the server isn't running
[/LIST]
 
**logout** - logs out the current user without logging out the administrator user or stopping the server

**suspend** - puts the server into sleep mode and logs out the user
    
[LIST]
[*]Do nothing and warn the user if the administrator user is logged in and the application running
[/LIST]
 
**help** - lists all commands and a short explanation

Other than this, the special user should not be allowed to do anything else, which includes connecting via (s)ftp or other protocols that would allow the person loggin in to circumvent any restriction.

As I said, this will probably require advanced scripting knowledge, and if this is not the right place to request this, please point me towards a better one to ask this. I'm currently using Ubuntu 16.04, but I'm willing to switch to any other operating system, if it helps with my request.

---

### Post by TheFu on 2017-10-07
Just make a shell that does this for yourself.  Setup the sudoers to only allow those specific commands with the specific options you want and put those into your shell.  Make that shell the shell for the userid allowed to login.  Be certain to capture all interrupts you don't want to be passed up.

The sshd_config file can limit who can use scp/sftp, but still connect over ssh.  ssh connections can force only 1 command to be run - this is how github works.  They only allow their "shell" to be run which allows git commands.

I don't have this itch, so hopefully this is enough background for you to make it yourself.
[http://atlantageek.com/2014/01/01/setup-script-login/](http://atlantageek.com/2014/01/01/setup-script-login/) might be helpful.  Just be certain to prevent cntl-c from breaking out of the menu.  The ABSG documents how to do that.

---

