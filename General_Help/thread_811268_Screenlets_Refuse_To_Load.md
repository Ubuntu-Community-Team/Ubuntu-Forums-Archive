---
title: "Screenlets Refuse To Load"
date: 2008-05-29
forum: General Help
---

### Post by JMorg on 2008-05-29
I have been trying for quite a while now to get have screenlets properly load and I can't quite seem to figure it out. I have been surfing the forums looking for a solution but have yet to find out. I have the program installed, however whenever I try to launch one of the screenlets I see nothing. For example, I select the clock screenlet and hit add/launch and nothing occurs. I have tried turning on the widget layer and still no go. Any help would be greatly appreciated because some of these screenlets seem to be pretty cool for customization purposes.

Thanks in Advance

---

### Post by Forlong on 2008-05-29
What version of Ubuntu are you using and how did you install Screenlets?

Also, what happens when running this in a terminal:
```
/usr/share/screenlets/Notes/NotesScreenlet.py
```

---

### Post by JMorg on 2008-06-03
> **Forlong said:**
> What version of Ubuntu are you using and how did you install Screenlets?

Also, what happens when running this in a terminal:
```
/usr/share/screenlets/Notes/NotesScreenlet.py
```

I'm using version 8.04 and I installed Screenlets via the Synaptic Package Manager. 

When I ran the code in a terminal it haulted with an Error13 stating that I did not have permission for NOTES.

---

### Post by Forlong on 2008-06-03
That's obviously the problem.
Try reinstalling Screenlets to restore the proper permissions.
If it doesn't help, post the output of
```
ls -l /usr/share/screenlets/Notes/NotesScreenlet.py
```
and
```
ls -ld /usr/share/screenlets
```

---

### Post by JMorg on 2008-06-06
> **Forlong said:**
> That's obviously the problem.
Try reinstalling Screenlets to restore the proper permissions.
If it doesn't help, post the output of
```
ls -l /usr/share/screenlets/Notes/NotesScreenlet.py
```
and
```
ls -ld /usr/share/screenlets
```

I reinstalled the program and the first line of code gives me:

-rwxr-xr-x 1 root root 14943 2008-05-27 18:50 /usr/share/screenlets/Notes/NotesScreenlet.py

The second line of code you asked me to run gives me:

drwxr-xr-x 53 root root 4096 2008-05-28 23:47 /usr/share/screenlets

Still not sure what's wrong, is there a while to recursively remove all of the Screenlets App and then do a reinstall through Synaptics Package Manager? Thanks again for your help and responses, I appreciate it.

---

### Post by Forlong on 2008-06-06
Looks good. You do have the permission to execute it.
Does it still complain, when running```
/usr/share/screenlets/Notes/NotesScreenlet.py
```
in the terminal?

---

### Post by JMorg on 2008-06-07
Yeah, unfortunately I'm still getting this:

OSError: [Errno 13] Permission denied: '/home/justin/.config/Screenlets/Notes'

---

### Post by Forlong on 2008-06-07
Aha, now that's a totally different error than how you described it before.
That's why it's always good to post the actual output.

You somehow messed with the permissions of your own home directory, so Screenlets is not able to store its settings.

Here's how to fix this:
```
sudo chown -R $USER:$USER $HOME
```
```
chmod -R u+rwx $HOME
```


Tip for the future: never run a command/application as root (sudo) that doesn't need it!

---

### Post by JMorg on 2008-06-24
Ah Thank you very much, it seems to have fixed my issue! Or for now at least lol.

---

