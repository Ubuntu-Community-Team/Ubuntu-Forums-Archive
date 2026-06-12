---
title: "Editing Unity launcher on guest account"
date: 2012-11-18
forum: General Help
---

### Post by Dacke on 2012-11-18
Edubuntu has a default guest account that students can use without being able to destroy anything. I'm trying to change the items displayed by default in the Unity launcher, but I'm not sure how to do it.

Any changes made from inside the guest account are reset on logout/login (as expected, that's the point of the guest account). The special [Edubuntu menu editing tools]("https://wiki.edubuntu.org/Edubuntu/Documentation/Edubuntu-menueditor") appear to be designed for Gnome2-style menus only.
[SIZE=1]
*(It would perhaps be better to phrase the question more generally as "how do I change things in an Edubuntu guest account?", but I thought I'd start out with something more specific.*)[/SIZE]

---

### Post by cwsnyder on 2012-11-18
Your best bet is to login as guest, then do your editing with sudo su [username] from the terminal, entering your administrator password for [username] account when requested.  You will have to enter your Linux commands from the terminal, but this should solve your permissions problem.

---

### Post by mc4man on 2012-11-18
You haven't mentioned what release of edubuntu as there would be major differences in how the default profile can be adjusted since unity first showed to now.

**In 12.10**
What shows in the Default launcher is determined by the key in 
/usr/share/glib-2.0/schemas/com.canonical.Unity.gschema.xml

If opened in a text editor (root to edit) you'll see the key/schema - 
    </key>
  </schema>
  <schema path="/com/canonical/unity/launcher/" id="com.canonical.Unity.Launcher" gettext-domain="unity">

Listed below between the <default> .... <default> are the default launcher icons.
You can carefully edit that list though a couple I wouldn't remove like 'unity://expo-icon'

You'd need to carefully look at how the key is written when  adding new .desktops,(if you are), follow exactly & **I'd advise backing up the orig. file 1st**.

When done you'd run this command to set the schema
```
sudo glib-compile-schemas /usr/share/glib-2.0/schemas
```

To return to the orig if needed  - edit the file back using the backup as a guide or just replace your edited file with the backup.
Then run the above command again to set.

---

### Post by Dacke on 2012-11-18
Thank you!

I'm using Edubuntu 12.04 LTS. But I'm prepared to switch to 12.10 if the new system is easier to work with?

---

### Post by mc4man on 2012-11-18
> **Dacke said:**
> Thank you!

I'm using Edubuntu 12.04 LTS. But I'm prepared to switch to 12.10 if the new system is easier to work with?
Easier? - maybe, haven't taken a look in 12.04 to see. Really just a matter of looking around & then a little T&E..

So in the case of 12.10 looked in synaptic for what unity package installed (nothing related), then unity-common where I saw the .xml
(so at this point easier because it's been found, ect.

In 12.04 it would likely be elsewhere, maybe some gconf related file??, unless it's hardcoded the file to edit can be found.

Further note on 12.10 - 
by default any other partitions would be shown in the Default unity profile inc. guest sessions.
To prevent that it's a bit further down the file, though it needs specific entries to work. There may be another setting somewhere that just does none, haven't looked.

Ex. I've 3 other partitions, so removed them from the launcher in my login, went to dconf-editor to get the key value, copied it into the .xml - as seen highlighted in screen
(orig value was []

If you make a mistake when compiling the schema the error will be noted & the file may be completely ignored. You would be well advised to fix pronto.

Ex. (ignore the blue, always says that
> $ sudo glib-compile-schemas /usr/share/glib-2.0/schemas
[sudo] password for doug: 
/usr/share/glib-2.0/schemas/com.canonical.Unity.gschema.xml: Error on line 67 char 1: 1-4:unknown keyword.  [COLOR="Red"]This entire file has been ignored.[/COLOR]
[COLOR="Navy"]No such key `computer-icon-visible' in schema `org.gnome.nautilus.desktop' as specified in override file `/usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override'; ignoring override for this key.[/COLOR]


After fixing my error, a good compile
> $ sudo glib-compile-schemas /usr/share/glib-2.0/schemas
[sudo] password for doug: 
No such key `computer-icon-visible' in schema `org.gnome.nautilus.desktop' as specified in override file `/usr/share/glib-2.0/schemas/10_ubuntu-settings.gschema.override'; ignoring override for this key.
doug@doug-XPS-M1330:~$ 


---

