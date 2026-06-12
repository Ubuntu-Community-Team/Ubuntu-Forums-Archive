---
title: "inittab gone ... do I create a file in /etc/init/?"
date: 2015-02-03
forum: General Help
---

### Post by Josiah_Philipsen on 2015-02-03
I know that inittab has been gone for a while, but I need to add some information into it or whatever is similar to it in Ubuntu 14.04. I know there is upstart and there is also files in /etc/init/. I am not sure where I need to add the information below or the format. Any assistance would be helpful.

[COLOR=#404040][FONT=Lato]Add the following line at the end of the /etc/inittab file:[/FONT][/COLOR]

```
[COLOR=#404040][FONT=Consolas]d1:23:respawn:/usr/bin/perl -w /usr/local/bin/nagios_dispatcher.pl --daemon --config /usr/local/etc/nagios_dispatcher.conf[/FONT][/COLOR]
```

I am following the instructions at this [website]("http://opm.readthedocs.org/opm-core/Installation.html") and I am at the point just above user interface. 

Thank you for your help in advance.

---

### Post by kjohri on 2015-02-04
/etc/init is the directory for upstart jobs. Try this link, [Starting Linux services with init scripts]("http://www.softprayog.in/tutorials/starting-linux-services-with-init-scripts").

---

