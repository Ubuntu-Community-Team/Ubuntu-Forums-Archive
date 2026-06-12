---
title: "Nautilus Error, bonobo-slay and 'Nautilus_Shell.server'"
date: 2008-02-10
forum: General Help
---

### Post by martron88 on 2008-02-10
Following a recent set of updates, nautilus was suddenly failing to start up on boot which left me without a gnome panel and access to most of my functions.  Having access to the terminal I spent a number of hours fixing the problem, mainly the file 'Nautilus_Shell.server' was suddenly missing.

Using Ubuntu Gutsy.

The error I would get on boot was:

```
Nautilus can't be used now. Running the command "bonobo-slay" from the console may fix the problem. If not, you can try rebooting the computer or installing Nautilus again.

Bonobo couldn't locate the Nautilus_shell.server file. One cause of this seems to be an LD_LIBRARY_PATH that does not include the bonobo-activation library's directory. Another possible cause would be bad install with a missing Nautilus_Shell.server file.

Running "bonobo-slay" will kill all Bonobo Activation and GConf processes, which may be needed by other applications.

Sometimes killing bonobo-activation-server and gconfd fixes the problem, but we don't know why.

We have also seen this error when a faulty version of bonobo-activation was installed.

```

I ran synaptic and re-installed nautilus-data which contains the Nautilus_shell.server file.  Then I ran the following to add the location to bonobo:

```
sudo bonobo-activation-sysconf --add-directory=/usr/lib/bonobo/servers

```

Next, I did a bonobo-slay and tried running nautilus from the command line and finally it worked!


I figured I would put this up here in case anyone else has similar problems.  Can't figure out why the .server file suddenly went missing or how bonobo's configuration lost the directory...

---

