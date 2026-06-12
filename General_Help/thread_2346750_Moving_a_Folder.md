---
title: "Moving a Folder"
date: 2016-12-18
forum: General Help
---

### Post by shane_faulkinbury2 on 2016-12-18
I'm trying to move a Flash plugin from my Downloads folder into the proper directory here /usr/lib/firefox-addons.  How do I do that?  I got this error.

---

### Post by yancek on 2016-12-18
The flashplayer directory appears to be in the Downloads folder under /home/bubba.  If that is correct, change to the /home/bubba/Downloads directory and run this command using the full filename of flashplayer.  I'm not sure why you want to do this.  There should be a readme.txt file in that directory which explains installing flashplayer:

> mv flashplayer /usr/lib/firefox-addons/

You used the tilde ( ~ ) symbol in front of /usr which is not correct.  That symbol refers only to the home directory of the user and should not be used otherwise.  You need to put the forward slash in fron of the /usr/lib otherwise it will look for a usr directory in the Downloads directory.

---

### Post by shane_faulkinbury2 on 2016-12-18
I'm trying to move libflashplayer.so to /usr/lib/firefox/browser.  What terminal command should I use?

o Identify the location of the browser plugins directory, based on your Linux distribution and Firefox version
    o Copy libflashplayer.so to the appropriate browser plugins directory.  At the prompt type:
        + cp libflashlayer.so <BrowserPluginsLocation>
    o Copy the Flash Player Local Settings configurations files to the /usr directory.  At the prompt type:
        + sudo cp -r usr/* /usr

When I try to do that I get an error.  Maybe I should be root!

---

### Post by howefield on 2016-12-18
> **shane_faulkinbury2 said:**
> When I try to do that I get an error.  Maybe I should be root!

You are trying to move a file into a system folder, so yes you need to precede the command with sudo.

Might be easier to install adobe-flashplugin for the latest flash rather than doing it manually unless you have a specific reason for doing it this way.

---

### Post by shane_faulkinbury2 on 2016-12-18
I get this and the instructions say nothing about how to put in the destination.

root@bubba-110-194:/home/bubba/Downloads/install_flash_player_11_linux.x86_64# mv -v libflashplayer.so
mv: missing destination file operand after 'libflashplayer.so'
Try 'mv --help' for more information.


mv --help
Usage: mv [OPTION]... [-T] SOURCE DEST
  or:  mv [OPTION]... SOURCE... DIRECTORY
  or:  mv [OPTION]... -t DIRECTORY SOURCE...
Rename SOURCE to DEST, or move SOURCE(s) to DIRECTORY.

Mandatory arguments to long options are mandatory for short options too.
      --backup[=CONTROL]       make a backup of each existing destination file
  -b                           like --backup but does not accept an argument
  -f, --force                  do not prompt before overwriting
  -i, --interactive            prompt before overwrite
  -n, --no-clobber             do not overwrite an existing file
If you specify more than one of -i, -f, -n, only the final one takes effect.
      --strip-trailing-slashes  remove any trailing slashes from each SOURCE
                                 argument
  -S, --suffix=SUFFIX          override the usual backup suffix
  -t, --target-directory=DIRECTORY  move all SOURCE arguments into DIRECTORY
  -T, --no-target-directory    treat DEST as a normal file
  -u, --update                 move only when the SOURCE file is newer
                                 than the destination file or when the
                                 destination file is missing
  -v, --verbose                explain what is being done
  -Z, --context                set SELinux security context of destination
                                 file to default type
      --help     display this help and exit
      --version  output version information and exit

---

### Post by shane_faulkinbury2 on 2016-12-18
> **howefield said:**
> You are trying to move a file into a system folder, so yes you need to precede the command with sudo.

Might be easier to install adobe-flashplugin for the latest flash rather than doing it manually unless you have a specific reason for doing it this way.

Sorry I do not know how to do this.

---

### Post by howefield on 2016-12-18
> **shane_faulkinbury2 said:**
> Sorry I do not know how to do this.

What, install adobe-flashplugin ?

Open the "*Software & Updates*" application and place a check in the Partners repository which you'll find in the "*Other Software tab*". Close out and accept the offer to reload your software sources. Open a terminal and type

```
sudo apt-get install adobe-flashplugin
```

---

### Post by shane_faulkinbury2 on 2016-12-18
I did everything you said reloaded my page and It didn't seem to work.  What could be wrong?

---

### Post by howefield on 2016-12-18
Firstly please post terminal output as text rather than posting an image and place the text between [noparse]```

```[/noparse] tags which will preserve the alignment and formatting of the text.

Secondly looks like you have flash installed successfully so close and restart the browser for the plugin to become active.

---

### Post by shane_faulkinbury2 on 2016-12-18
Thanks a lot howehield!  I didn't realize I had to restart the browser!

---

### Post by howefield on 2016-12-18
Cool, glad you got it and thanks for marking as solved.

---

