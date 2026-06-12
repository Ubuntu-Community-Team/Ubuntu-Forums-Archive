---
title: "Create a User Profile for Kids and Limit Available Applications"
date: 2014-11-10
forum: General Help
---

### Post by xmbwd on 2014-11-10
I am trying to create a kiosk mode for a second user in Ubuntu, where that second user has access only to a limited set of applications.  Basically, I am trying to make my main Ubuntu computer accessible to my young child, but not giving full access to all the applications.

As stated [here]("http://www.alandmoore.com/blog/2013/02/13/building-a-linux-system-for-a-child-part-3-security-concerns/"), it appears that > History is littered with projects that attempted to do this  (gnome-nanny, timekpr, Ubuntu Christian-Edition’s parental controls),  but were subsequently abandoned, obsoleted by developments in desktop  environments, or never released to more than a single distro.

Is there no current program or other way to create essentially a Cafe-mode in Ubuntu -- so that only a select group of applications are available???

What I've found so far:

[LIST=1]
[*][Instructions]("http://www.instructables.com/id/Setting-Up-Ubuntu-as-a-Kiosk-Web-Appliance/?ALLSTEPS") on creating a single-application (Chrome) kisosk, which would be great if I only had one application 
[*][Instructions]("http://ubuntuhandbook.org/index.php/2014/05/install-users-groups-management-tool-ubuntu1404/") on installing "Users and Groups" (advanced user privilege settings) to limit access to things like storage devices, printers, system logs, etc. 
[*][Instructions]("http://www.omgubuntu.co.uk/2014/05/timekpr-restrict-computer-access-ubuntu") to install "Timekpr" to restrict hours of use per day, and days per week the computer is available 
[*]Open-DNS is an easy way to filter web content -- I also use Tomato and dd-wrt, which allow per ip-address limitations 
[*][gnome-nanny]("https://wiki.gnome.org/Projects/Nanny") and [pessulus]("https://wiki.gnome.org/action/show/Apps/Attic/Pessulus?action=show&redirect=Pessulus") are deprecated 
[/LIST]

As Ubuntu becomes more and more accessible and usable, it seems logical that this capability needs to be present so that parents can limit access to kids -- and hotel/cafe/library/school admins can present a bucket of outward-facing applications.  

Please let me know if I am missing something?

Relatedly, one alternative that I thought of was to create a Kiosk mode for VirtualBox for the kid's user login (that is, when he logs in, there is only one option --> VirtualBox, and only one choice:  one of [these]("http://opensource.com/education/14/1/teaching-kids-linux") (or [these]("http://www.brighthub.com/computing/linux/articles/43224.aspx")) "kid-friendly" desktop environments). Is that more feasible?  Or would it be impossible to limit access to the settings in Virtualbox?

---

### Post by dragonfly41 on 2014-11-10
You don't give the age of the child(ren).
Children can be very inventive in getting around user login details. Spotting you typing in.
My vote would be to totally separate operating systems (adult/child) into a dual boot configuration.
This does require reboot between adult/child usage but offers more separation.
You can supplement dual boot with OpenDNS account.
Have you considered getting child interested in Raspberry Pi programming?

---

### Post by xmbwd on 2014-11-10
Ages 4-7.  I agree kids are good at getting around controls -- right now I think I'm ok.  When they get to be old enough, a dual-boot solution could work -- though optimally there would be an option that avoids losing any active session I have going.  At their current ages, a dual boot would be a little much.  

When they are old enough, Raspberry Pi is DEFINITELY going to happen.  No question about that.  I'm just trying to get them a baby step first. 

I'm hoping there is another solution.  At a minimum, I'd like to figure out a kiosk solution using VirtualBox.

---

### Post by O9aIevckc0 on 2014-11-10
have you tried simply removing programs from the menu including the menu editor and makeing the config file for whatever menu non writeable for the child user  ?

though once they get older you may have to just get them their own pc as kids can get round nearly anything after about 12-13 if they want to
(i used to look for ways to beat the filter back in school and its not hard :lol:)

---

### Post by xmbwd on 2014-11-10
Sorry to be daft, but could you elaborate on that?

> **abpabp said:**
> have you tried simply removing programs from the menu including the menu editor and makeing the config file for whatever menu non writeable for the child user  ?


---

### Post by O9aIevckc0 on 2014-11-11
what Desktop enviroment do you use ?  

as for makeing it non writeable    chmod a-w whateverconfigfile

---

### Post by xmbwd on 2014-11-11
I use base Ubuntu, so Gnome Desktop with Unity shell.  Now that I think about it, I could auto hide the Launcher and use Cairo-Dock -- which I can then lock (because you can't remove the home "BFB" button in Unity).  That may be enough.  I'm going to go try it and report back.

---

