---
title: "Administrating many Ubuntu desktop computers?"
date: 2008-01-17
forum: General Help
---

### Post by johann_p on 2008-01-17
I am wondering about whether Ubuntu could be the right choice as the OS for a medium-size installation with several dozen to hundreds of desktop computers (several servers in addition, but those are not really the issue here).

The following things should be possible for this:
* Create some script or configuration files that provide a standard-installation that differs from what the default installation does - automate it so that only at specific points manual intervention is needed.
OpenSuse has the option to save all the responses given to the installer in a config file that can then be used at later installations to automate the process. Is this possible in Ubuntu?

* Make it easy to perform the same installation and configuration steps on groups of computers. Essentially the administrator should be able to install packages, perl cpan packages, ruby gems, separate software so that the very same actions are taken on all or a group of the computers automatically (it wouldnt be feasable that he goes around and reapeats the same steps on dozens or hundreds of computers)

* Don't let end users mess with the configuration: in order to make that many computers administrateable, end users should not be able to do any configuration changes unless explicitly authorized by the administrator. This includes especially the update-manager:

* updates should be carried out by the administrator only: there should be no notification of security updates or similar on the desktop of end-users. The administrator should be able to easily do security updates on all the computers simultanously and automatically.

* Use a server-based authentification scheme and allow users to share server-based resources like raid storage, printers, etc. while these resources should be administrateable centrally. So if a new user is added, it should be automatically added to all computers and have the same rights on all of them. If a new printer is added to the network, it should get configured in an identical manner on all computers etc.

* Make dist-upgrade in a painless manner: I am a bit concerned about this one since I had been using Ubuntu privately for quite a while now (on several computers) and ALWAYS had problems with the dist-upgrade. This would of course be totally unacceptable in a situation with many centrally administrated computers.

Can somebody point me in the right direction for how all this is supported in Ubuntu or tell me if it is supported at all?

I am talking about this on a more theoretical level for now as we are still in the planning phase and not sure about the OS to go with, but in order to make a decision for any OS, all thses issues must be demonstratable on a small sample installation here.

---

### Post by johann_p on 2008-01-17
Is there a better forum for asking this kind of question? :confused:

---

### Post by fjgaude on 2008-01-17
You might cut and paste your post to the Ubuntu Servers and Security forum here.

---

### Post by johann_p on 2008-01-18
> **fjgaude said:**
> You might cut and paste your post to the Ubuntu Servers and Security forum here.

Thank you for the suggestion, have done that now!
I was reluctant because my questions are not really about servers or security, but on the other hand there does not seem to be a forum that is really geared towards the needs of administrators who need to keep installations of many Ubuntu desktops running.

I had been hoping that that (using Ubuntu in smaller companies etc.) would actually be something that is being done quite often in the meantime, no?

---

