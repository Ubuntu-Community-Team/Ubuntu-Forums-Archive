---
title: "Prevent normal users from shutting down"
date: 2006-11-02
forum: General Help
---

### Post by NetworkGuy on 2006-11-02
Hi All,

I've searched but couldn't find the answer to this question:

In Ubuntu, how can I prevent someone with a normal user account (no admin access) from being able to shut down or reboot the computer from X?

I have a computer on-line that needs to remain up 24/7.  However I also have two users that may need access to this box.  While I have removed what the user doesn't need to see from X, I can't figure out how to stop the user from rebooting or shutting down the physical computer.

---

### Post by rattking on 2006-11-02
Hi
I know in kubuntu the option lies in the kdm login manager under system settings.. 
there's probably a similar setting for gdm the Gnome login manager
I'm just not sure where that's located in gnome

---

### Post by NetworkGuy on 2006-11-03
I looked in the Gnome login manager and didn't see anything related to logoffs.

---

### Post by rattking on 2006-11-03
I dont have gnome installed to test this.. but it seems like what your looking for
[http://www.gnome.org/projects/gdm/docs/2.16/configuration.html](http://www.gnome.org/projects/gdm/docs/2.16/configuration.html)

HaltCommand
HaltCommand=<sbin>/shutdown -h now
 Full path and arguments to command to be executed when user selects "Shut Down" from the Actions menu. This can be a ';' separated list of commands to try. If a value is missing, the shut down command is not available. Note that the default for this value is not empty, so to disable "Shut Down" it must be set to an empty value.

and

RebootCommand
RebootCommand=<sbin>/shutdown -r now
 Full path and optional arguments to the command to be executed when user selects Restart from the Actions menu. This can be a ';' separated list of commands to try. If missing, the restart command is not available. Note that the default for this value is not empty so to disable restart you must set this explicitly to an empty value.

---

### Post by NetworkGuy on 2006-11-03
I saw that in the /etc/gdm/gdm.conf file, but I think that will remove the command for all users.  

I want the command to be available for the administrator of the machine.  But if the administrator has to launch sudo shutdown -h now from the terminal, so be it.

---

### Post by jordilin on 2006-11-03
Here there's a complete howto for Ubuntu:
[http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/](http://ubuntu.wordpress.com/2006/03/20/disable-shutdown-for-normal-users/)

---

### Post by NetworkGuy on 2006-11-03
Sweet..  

Thanks Jordilin.  Looks like this should do the trick..

---

### Post by escape on 2006-11-03
I was gonna post to use Beryl on an ATI card (hurrr), but guess you've got a more practical solution.

---

### Post by NetworkGuy on 2006-11-03
The machine is being used as a server.  Loading Beryl would have been overkill.  But thanks for the suggestion regardless.

---

### Post by carolinason on 2007-05-10
So, I take it that there is no way to exclude the Restart and Shutdown options from the *exit panel* in Gnome (Is the *exit panel* a part of GDM?). I would like to exclude these options for certain users.

The howto
[http://ubuntu.wordpress.com/2006/03/...-normal-users/](http://ubuntu.wordpress.com/2006/03/...-normal-users/)

doesn't really answer this question even though, it is a workaround. The end of the howto is incorrect in halting the system, the command provided reboots the system.

I have googled and read for hours, but am unable to get a definitive guide to administrate this issue.

Thank you-

---

### Post by zvacet on 2007-05-10
To use shutdown comand you have to be root (member of admin group),and as normal users can not use sudo or become root they can not use shutdown command.

---

