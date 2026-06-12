---
title: "Problems using gksu and pkexec"
date: 2018-08-27
forum: General Help
---

### Post by MJae on 2018-08-27
I've been trying to launch Thunar using gksu and pkexec because some of my themes (which aren't working anymore after upgrading to 18.04) are in /usr/share/themes/ and I wanted to remove them. However, I can't launch using gksu nor pkexec. Using gksu from terminal does not work because I can't enter the password since the focus cannot set to the password box. On Alt+F2, I can enter the password, but I get nothing. Using pkexec that way results in the same. Using pkexec on the terminal gives me this:

```
Invalid MIT-MAGIC-COOKIE-1 keyThunar: Cannot open display: 
```

Are they not supposed to work anymore? What should I do instead?

---

### Post by wildmanne39 on 2018-08-27
Hello, please try;
```
sudo -H
```
Thanks

---

### Post by MJae on 2018-08-27
[FONT=courier new]sudo[/FONT][FONT=courier new] -H[/FONT] gives me this:
```

usage: sudo -h | -K | -k | -V
usage: sudo -v [-AknS] [-g group] [-h host] [-p prompt] [-u user]
usage: sudo -l [-AknS] [-g group] [-h host] [-p prompt] [-U user] [-u user] [command]
usage: sudo [-AbEHknPS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt]
            [-T timeout] [-u user] [VAR=value] [-i|-s] [<command>]
usage: sudo -e [-AknS] [-r role] [-t type] [-C num] [-g group] [-h host] [-p prompt]
            [-T timeout] [-u user] file ...

```
[FONT=courier new]sudo[/FONT][FONT=courier new] -H [/FONT][FONT=courier new]thunar[/FONT] gives me this:
```

No protocol specified
Thunar: Cannot open display: 

```

---

### Post by wildmanne39 on 2018-08-28
You need to run:
```
sudo -H
```
with the app name that you want to open, for example:
```
sudo -H Thunar
```
I do not use xubuntu often so I am not sure if thunar is capitalized or not.

---

### Post by wildmanne39 on 2018-08-28
I installed xubuntu in virtualbox and the following command does work.
```
sudo -H thunar
```

---

### Post by sudodus on 2018-08-28
```
sudo -H thunar
```

works for me (in a persistent live Xubuntu 18.04.1 LTS). See the attached screenshot.

Something else must be wrong in your system. Upgrading from one version to another one is always risky because some things from the old version may still be there and cause problems.

---

### Post by The Cog on 2018-08-28
$ file /usr/bin/Thunar
/usr/bin/Thunar: symbolic link to thunar

"sudo -h thunar" works for me. However, try:
```
sudo -i
thunar
```

---

### Post by MJae on 2018-08-28
Capitalized or not, I'm still getting this same response:
```

No protocol specified
Thunar: Cannot open display: 

```

Same output with the [FONT=courier new]sudo[/FONT][FONT=courier new] -[/FONT][FONT=courier new]i[/FONT] then [FONT=courier new]thunar[/FONT].

---

### Post by sudodus on 2018-08-29
Something else must be wrong in your system. Upgrading from one version to another one is always risky because some things from the old version may still be there and cause problems.

You can try to repair it,

```

sudo apt purge thunar

```

and make sure that all files in your home directory associated with thunar (also hidden files) are owned by your user ID (not owned by root).

From **man apt**

>    install, remove, purge (apt-get(8))
       Performs the requested action on one or more packages specified via
       regex(7), glob(7) or exact match. The requested action can be
       overridden for specific packages by append a plus (+) to the
       package name to install this package or a minus (-) to remove it.

       A specific version of a package can be selected for installation by
       following the package name with an equals (=) and the version of
       the package to select. Alternatively the version from a specific
       release can be selected by following the package name with a
       forward slash (/) and codename (stretch, buster, sid ...) or suite
       name (stable, testing, unstable). This will also select versions
       from this release for dependencies of this package if needed to
       satisfy the request.

       Removing a package removes all packaged data, but leaves usually
       small (modified) user configuration files behind, in case the
       remove was an accident. Just issuing an installation request for
       the accidentally removed package will restore its function as
       before in that case. On the other hand you can get rid of these
       leftovers by calling purge even on already removed packages. Note
       that this does not affect any data or configuration stored in your
       home directory.


```

sudo apt install thunar

```

[hr][/hr]
If still no luck, I think you should backup all important files to another drive, and after that make a **fresh installation** from a 18.04.1 LTS iso file.

---

### Post by MJae on 2018-08-29
No good. Same response after purge, then install.

[FONT=courier new]No protocol specified
Thunar: Cannot open display: 
[/FONT]
Is there anywhere else I can look which might be causing this? Or anything else I can try? I'm not at liberty to do a fresh install because this is my one computer and I need it for work. While it's the Windows side I use for work, it will still require a significant amount of time to get this setup back if I come from a fresh install.

---

### Post by sudodus on 2018-08-29
> **MJae said:**
> No good. Same response after purge, then install.

[FONT=courier new]No protocol specified
Thunar: Cannot open display: 
[/FONT]
Is there anywhere else I can look which might be causing this? Or anything else I can try? 

I am sure there is. *But I don't know where to look or what else to try.* If you are lucky, someone who knows, will see this and help you.

---

### Post by Holger_Gehrke on 2018-08-29
I can think of three things you might try.


[LIST=1]
[*]Start Thunar normally and use the 'admin://' schema in the location field; the two slashes are part of the schema, so to access /usr/share/themes you would enter 'admin:///usr/share/themes' (three slashes). This is somewhat more restricted than a true 'root'-filemanager, but while testing it I could remove the file I created with 'sudo touch /usr/share/themes/test.txt' 
[*]Allow root to access the X-Server with 'xhost +si:localuser:root'. This should at least get rif of the message 'Cannot open display'. 
[*]Check whether the environment variables DISPLAY and XAUTHORITY and their values are available when doing 'sudo'. Examine the output of 'sudo env' or of 'sudo sudo -V'. The latter shows a lot of  data on the workings of sudo ... If they are not, you should carefully read 'man 5 sudoers' and then 'sudo visudo'. 
[/LIST]
 
If these don't help, you could just use the shell or the Midnight Commander (mc, a file manager running in a terminal) to erase the themes, If doing a clean install is not an option currently.

Holger

---

### Post by MJae on 2018-08-29
> **Holger_Gehrke said:**
> I can think of three things you might try.


[LIST=1]
[*]Start Thunar normally and use the 'admin://' schema in the location field; the two slashes are part of the schema, so to access /usr/share/themes you would enter 'admin:///usr/share/themes' (three slashes). This is somewhat more restricted than a true 'root'-filemanager, but while testing it I could remove the file I created with 'sudo touch /usr/share/themes/test.txt' 
[*]Allow root to access the X-Server with 'xhost +si:localuser:root'. This should at least get rif of the message 'Cannot open display'. 
[*]Check whether the environment variables DISPLAY and XAUTHORITY and their values are available when doing 'sudo'. Examine the output of 'sudo env' or of 'sudo sudo -V'. The latter shows a lot of data on the workings of sudo ... If they are not, you should carefully read 'man 5 sudoers' and then 'sudo visudo'. 
[/LIST]
 
If these don't help, you could just use the shell or the Midnight Commander (mc, a file manager running in a terminal) to erase the themes, If doing a clean install is not an option currently.

Holger

Thanks a bunch! The first one worked with the original point of my post, I was able to delete the themes which stopped working. The second one, I'm not so sure... I am now able to run [FONT=courier new]sudo[/FONT][FONT=courier new] -H [/FONT][FONT=courier new]thunar[/FONT] with the expected output but, upon inspection as suggested in #3, it says [FONT=courier new]DISPLAY=:0[/FONT]. That looks odd, but I'm not sure what's supposed to be here and, sometimes, counting starts from 0.

Here are the complete outputs:
[LIST]
[*][FONT=courier new]sudo[/FONT][FONT=courier new] env[/FONT] - [https://pastebin.com/RBg4QLEW](https://pastebin.com/RBg4QLEW)
[*][FONT=courier new]sudo[/FONT][FONT=courier new] [/FONT][FONT=courier new]sudo[/FONT][FONT=courier new] -V[/FONT] - [https://pastebin.com/KEQ0Vk3w](https://pastebin.com/KEQ0Vk3w)
[/LIST]

The workarounds are fine, but there is still a problem. Also, I have not been able to launch notes and the greeter settings app. It might be related. This is what I get for notes:

```
(xfce4-notes:12606): GLib-GIO-CRITICAL **: 11:40:29.249: g_dbus_proxy_new: assertion 'G_IS_DBUS_CONNECTION (connection)' failed
```

I thought I could launch it again after executing the command in #2 but it still doesn't run.

---

### Post by Holger_Gehrke on 2018-08-30
The DISPLAY variable is okay the way it is, the count of displays does indeed start at 0. The full format for DISPLAY is 'server:display.screen' with server defaulting to localhost and screen to .0.
What is missing from the output of env is XAUTHORITY which should give the location and name of the file with the 'magic cookie' used to authorize a user to the server. This should normally be '/home/mjae/.Xauthority'. The output of 'sudo sudo -V' says it would pass that variable, so it's probably not set or not exported. Check whether the variable is set with 'echo $XAUTHORITY' and check whether the file '~/.Xauthority' exists (remember, files with a dot at the beginning of their name are hidden, so either use 'ls -a ~' or hit ctrl-h in Thunar to show hidden files).

And yes, the dbus problem might indeed be related. dbus is a messaging system for programs to communicate with each other which can also start programs if another program sends a message to them and they aren't running yet and passes along an environment to them which should normally contain XAUTHORITY. If dbus is not running or not working quite right that could be the source of the problem. Sadly I don't know enough about dbus to help with that.

Holger

---

