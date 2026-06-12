---
title: "Uninstalling a .deb package created from an RPM"
date: 2014-05-12
forum: General Help
---

### Post by shlema on 2014-05-12
I have a strange problem with uninstalling a package. What I did was to create a .deb package (Audacious 3.5) from an .rpm with alien and to install it then. The resulting application wouldn't start correctly with output like this: 

> shlema@shlema-T420:~$ audacious 
FATAL: No output plugin found.
String leaked: replay_gain_album
String leaked: sw_volume_left
String leaked: FALSE
String leaked: Hotkey_0_key
String leaked: eqpreset_default_file
String leaked: Hotkey_1_key
String leaked: 0,0,0,0,0,0,0,0,0,0
String leaked: convert_backslash
String leaked: 174
String leaked: player_width
String leaked: wed_m
String leaked: equalizer_active
String leaked: thu_m
String leaked:  - 

&#8230;and a few dozens of similar strings.

So I tried to remove the package (there was no trace of any audacious packages in Synaptic), but apparently it didn't work &#8212; I can still run the command 'audacious' from the terminal with the same weird output. Installing other versions of Audacious (from native .debs) doesn't help at all.

What am I missing here? 

Thanks.

---

### Post by Kirboosy on 2014-05-12
Lets try and located this package.

I personally use something like this to find a package that is installed on my system through apt-get

```
dpkg --get-selections | grep audacious
```

Does that return anything? If nothing returns you might want to play with the keyword you are grepping for. Also if you remove the grep it will display all packages installed on system.

Hope that helps!
~Caboose

---

### Post by shlema on 2014-05-12
There were two plugin-related packages, but uninstalling them didn't solve the issue. I also tried to install and uninstall the package that seemingly has caused the problem again, but it changed nothing.

So, right now I can see no trace of any audacious-related package in the system, but running the command still returns that weird output.

---

### Post by Kirboosy on 2014-05-12
Why did you install the RPM to deb converted package in the first place? It looks like they have a PPA with the most recent version for Ubuntu.

[https://launchpad.net/~nilarimogard/+archive/webupd8](https://launchpad.net/~nilarimogard/+archive/webupd8)

When you removed the package how did you do it?

```
whereis audacious
```

That will locate the binary, source, and manual page files for a command.

~Caboose

---

### Post by shlema on 2014-05-12
I didn't know about that repo then, so it's definitely my bad. 

I removed the packages with $sudo apt-get remove --purge %package_name%.

Now, here's the trace:

> shlema@shlema-T420:~$ whereis audacious
audacious: /usr/local/bin/audacious


Should I just remove this binary?

---

### Post by Kirboosy on 2014-05-12
Papibe has suggested that you try using the following command

```
sudo dpkg -r <originalFileName.deb>
```

See if that gets it removed any further. I think the last thing to try would be to manually remove the binary. I just don't want to break your package manager.

~Caboose

---

