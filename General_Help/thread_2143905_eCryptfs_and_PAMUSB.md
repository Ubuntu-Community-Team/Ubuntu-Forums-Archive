---
title: "eCryptfs and PAMUSB"
date: 2013-05-10
forum: General Help
---

### Post by nybble110 on 2013-05-10
First, I appreciate any help that anyone can offer.  I've searched for a while with no real answer to my issue.

First the basic software/hardware rundown:

Ubuntu 12.04.2 running on VMware Workstation (4 vCPU, 2GB RAM, 64GB HDD)
PAM_USB v0.5.0 (Installed from repositories)

My problem is this:

I have successfully configured PAMUSB to authenticate against a USB flash drive connected to the system.  

If I attempt to log on to my desktop, my username simply has a "Log In" button under it, which I expect as long as the flash drive is connected, but when I click "Log In" the window manager flashes for a second and then drops me back to a login screen.  I suspected this was due to my home directory not being mounted since it was encrypted.

If I log in through a TTY session, PAMUSB successfully processes my login request but, I am presented with:

Signature not found in user keyring.
Perhaps try the interactive `ecryptfs-mount-private`

Running this command prompts me for my system password, which once entered, mounts my home directory as expected.

If I leave this TTY session active, switch back to the GUI, and click "Log In", everything works fine.

Is there any way to eliminate the necessity to run `ecryptfs-mount-private` and leave an extra TTY session running?

Again, thanks for your help.

I can post logs and configuration files if needed.

---

### Post by Githlar on 2013-09-27
After struggling with this for a couple days I finally came up with a solution to this problem. I hit many, many stumbling blocks while going about this, but in the end I'm proud of how short and sweet it really is.

First and foremost, there are a couple of issues with this:
[LIST=1]
[*]Gnome keyring does not unlock. You can log in just fine, but quite a while after you've logged in you may be asked for you password to unlock the Gnome keyring. Unfortunately, there's no way to solve this that I have found since Gnome keyring doesn't allow you to unlock it via the command prompt.
[*]It breaks pam-auth-update. This means that if you ever install or remove any PAM modules, you will have to update the configuration files by hand. I haven't found any way around this.
[*]As it is laid out, it requires you to store your password in a file on the USB device. Than can be changed within the script, but I'll leave that as an exercise for you. I've given some hints to improve security in the script comments.
[/LIST]

First thing's first, we need to make a udev rule. Since it's a USB drive, we need to make sure that it's always mounted in a consistent place. I chose to give mine the device name /dev/cryptusb.

/etc/udev/rules.d/70-crypt-usb.rules:
```

BUS=="usb", KERNEL=="sd*",
ATTRS{model}=="USB2FlashStorage", ATTRS{vendor}=="Ut165", NAME:="cryptusb%n",
SYMLINK+="%k", GROUP="your_username", OWNER="your_username"

```

You will have to replace ATTRS{model} and ATTRS{vendor} with the information pertaining to your flash drive. If you're setting this up for multiple users and they all have the same model of flash drive, you may want to add ATTRS{serial_short} as well. All of this information can be found in /etc/pamusb.conf once the device is added to the system, or by using `udevadm info --query=property --name=/dev/sdX`. Once you've added the rules, simply remove and re-insert your flash drive and you should see files called /dev/cryptusb and /dev/cryptusb1.

Now that we've gotten our udev rules in place, it's time to write a PAM script.

/usr/share/pam/usb-auth-ecryptfs (you can put it anywhere you wish):
```

#!/bin/bash

PAM_HOME=$(cat /etc/passwd | grep $PAM_USER | cut -f6 -d:)

if [ "$PAM_TYPE" == "open_session" ] && [ -e $PAM_HOME/.ecryptfs/auto-mount ] && [ -b /dev/cryptusb ] && [ -s $PAM_HOME/Access-Your-Private-Data.desktop ]; then
   #In order to be able to mount eCryptFS, we have to have the passphrase.
   #eCryptFS encrypts the mount passphrase with your login password. It
   #is also unfortunate that eCryptFS also requires the password/passphrase
   #to be TYPED into some tool. This means we need a plaintext password or
   #passphrase available to pass through the tools. So, I put a file on my
   #USB subtly called "password". The contents of this file is passed
   #though the eCryptFS tools to get the unwrapped passphrase and then
   #set the keys needed for encryption.
   #This is obviously a security risk, but I was trying to throw this
   #together as quickly as possible (it still took a couple days since
   #I needed to learn everything about PAM). However, what someone might
   #do is store a unique GPG key somewhere on their machine in an
   #unencrypted area. They could then encrypt the password file with the
   #GPG key (it would have to be passwordless). They would pass the file
   #though GPG, and then pass that output into the eCryptfs tools.
   #I also thought it would be even less conspicuous if the password
   #(even GPG encrypted) were stored in un-partitioned spaced on the USB
   #and then read in with dd. In that case threre wouldn't even be a file
   #to arouse suspicion if your USB were ever stolen and you can avoid
   #the mount and umount commands in the script.

   #The name of the password file
   pass_file="password" #will be (usbroot)/password

   #Try to mount the default USB drive location, partition 1 onto /mnt.
   #If that doesn't work, look in $HOME/.ecryptfs/usb.device for a file
   #whose contents contain a udev-named device without the /dev portion
   #(the file would contain  "cryptusb" -- no quotes --  by default, i.e.)
   #I used /mnt because the entire root folder is never used that I'm
   #aware of in Ubuntu. On top of that, it's just a quick mount and then
   #unmount operation.
   mount /dev/cryptusb1 /mnt
   if [ $? -ne 0 ]; then
      if [ -e $PAM_HOME/.ecryptfs/usb.device ]; then
         mount /dev/$(cat $PAM_HOME/.ecryptfs/usb.device) /mnt
         if [ $? -ne 0 ]; then
            exit 3
         fi
      else
         exit 3
      fi
   fi

   #pam_exec runs this as root, even with the seteuid command so have to
   #sudo it to get the keys loaded to the proper user.
   sudo -u $PAM_USER /bin/sh -c "ecryptfs-unwrap-passphrase $PAM_HOME/.ecryptfs/wrapped-passphrase - < /mnt/$pass_file | ecryptfs-add-passphrase --fnek -;mount.ecryptfs_private"

   umount /dev/cryptusb1
fi

exit 0

```

Make sure you make it executable: `sudo chmod +x /usr/share/pam/usb-auth-ecryptfs`

Finally, it's time to do some adjustment to PAM.

Add the following line at the end of the config file /etc/pam.d/common-session:
```
session [default=ignore]		pam_exec.so /usr/share/pam/usb-auth-ecryptfs
```

This line tells PAM to run the script created above when a user starts and stops a session of any kind (terminal or GUI). The script itself, however, only executes on session start.

Then add this line to /etc/pam.d/common-session-noninteractive above the line that says "session	optional	pam_ecryptfs.so unwrap":
```
session	[success=ignore default=1] pam_succeed_if.so service != sudo
session	optional	pam_ecryptfs.so unwrap #This line is already present in the file
```

This was one particularly tricky part. Since the script above runs as root (even with pam_exec's seteuid option...), I have to execute stuff intended for the user with sudo. The problem was, every time I left a sudo instance ("session"), my encrypted drive would dismount. So, I had to hack PAM a little bit in order exclude the call to the ecryptfs mount/unmount if -- and only if -- it was within a sudo session.

However, looking at it now it appears that (in my installation) cron, samba and sudo all use that line. Cron doesn't need to log in as you since it's runs a setuid sub-process anyway, sudo does the same thing, but samba's a little iffy depending on how you have it set up. I think any normal user could actually just remove the pam_ecryptfs.so line from /etc/pam.d/common-session-noninteractive and suffer no consequences. Both of those options, though, still break pam-auth-update. However, for the sake of maximum compatibility, the above solution would be the best bet.

And there you have it! I tested this pretty well to ensure that it works for both console and GUI logins. Now you can log in with just your USB stick inserted!

---

