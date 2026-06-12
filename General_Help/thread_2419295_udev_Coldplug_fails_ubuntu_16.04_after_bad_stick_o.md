---
title: "udev Coldplug fails ubuntu 16.04 after bad stick of memory"
date: 2019-05-19
forum: General Help
---

### Post by alpeterson on 2019-05-19
Since kubuntu has moved on to Plasma5,  We have been stuck on Ubuntu 16.04 because it has a working KDE4.

but then a memory stick has failed, and there must have been some corruption during installation..

I swapped the memory and the hardware seems ok, it passes memory tests now...

but udev Coldplug is giving all kinds of errors.

[https://photos.app.goo.gl/wTPBQD3VCesHGXQ9A](https://photos.app.goo.gl/wTPBQD3VCesHGXQ9A)

I tried rebuilding initrd... I tried using dpkg to reinstall and reconfigure udev and stuff... but udisks2 won't install and things like the hard drive don't get properly caught.

There is diskspace... but udev won't automatically get stuff going...

to get the device online I had to go to recovery (because I stupidly installed gnome and it's display manager captures the keyboard and won't let me login when it fails..) is borked without the driver) start the networking modprobe tg3 ifconfig eth0 up.. and then I'm online.. if I modprobe i915 I can startx     I have uninstall gir*-gdm and all gdm stuff, so next reboot I should be able to get in.

I tried dpkg-reconfigure and dpkg -i all of the files in the cache, but that stupidly reinstalled gnome after I reinstalled. it.. and I never intend to use gnome again after the display manager doesn't handle a failure gracefully.

So I can manually modprobe stuff and get stuff except for the display manager kubuntu expects...  See the google photos link... It's really frustrating and I'm going to have to get another hard drive going because of this and most forum posts about this issue were in about 2010... but I think all I need is a command to reinstall all the packages already on the system... and reconfigure them... there is NO custom configuration (outside the home directory) so I should be able to just get online and type a command as root, and it should all come back up.

I do have a bunch of xental backports  multiverse and such repos enabled, but it appears that nothing is installed from them because when I disabled them and reenabled them nothing changed with suggested versions of software.

the udisks2 complains that there is no amd64 version of it and no file... but it also says it is installed as the latest version...

The kernel is 4.4.148  I believe...  see photo galallary..

This computer has been in use for about the last 3 years and it is well configured and has been working reliably...  I am getting ready to install the "10 year LTS" version but I have to figure out how to get KDE4 instead of the completely borked KDE5 which borks when screen resolution changes and shows the wrong icons in the menu... "by design"

thats coldplug not coldboot

[https://ubuntuforums.org/showthread.php?t=1567147](https://ubuntuforums.org/showthread.php?t=1567147)   This appeared to be related, but it didnt help

[IMG]https://lh3.googleusercontent.com/9YV9zvSAlH1thw6-uCoYUdQ4lqHbOUrPgrbXEPzGopPiGKPR3rFDs9V691O5eRPJxC8XFOsQOgBejGdtYNoRIf3mfQJgkJwnnqcwWIX0bg3_cZ1G_ewIuxxhZGH9Kq0KLA0A9zFY2JoOl5DkiZK67kZdbcJVur5uidg_kAykh48QqU3-1tj-3EcCGzjlCkjOvWKwA8PuLnc8lhhj8CTlCRNGOtU2PsgGC-yAf0vwERw3mafiUKdcxCaycK8sTCcGWm9Sl9DJGhHx_8saa5B3-PSgxGevFSiK2p4YJ5x2dqJMmD4WKDWETdwk2gEagkzhVZUT6BHQhAV0exBMy9dsjfOIiNUZaKYlT7gC7PhPZ4_rWbsUxe0JZsCop5shcwMq-tV4_-8VRzjkYqRvaANdobhWAh0YOlmgx5kSoCsB0w70TncdnUWkXErYpzR11SO4GXrfycJSEC4rxe5tIBmIIDfXI8Twh5yWbAuUHMYGvocqD5mOlP_dUVMBcssvW-PiJoxLxQNK7yuP88bYICDuYbBDzlkcnVAajFWfqtTIHc35U8iGepT1_J4_giZu1nIzHoKS2Hc2covDV6UQkGxrkagbn0tLS8xTsbdWp0C4gsxzEmZynBddC1o3NedKAj8e4Kykh64tQx-NjaU8JgmSkVA1NzacCWjS=w1276-h958-no[/IMG]

---

### Post by Xian on 2019-05-20
> [COLOR=#000000]I think all I need is a command to reinstall all the packages already on the system... and reconfigure them... there is NO custom configuration (outside the home directory) so I should be able to just get online and type a command as root, and it should all come back up.[/COLOR]

My remarks only pertain to your quoted comments shown above. 

The program aptitude can reinstall all the pacakges already on your system. 
But it _must_ have access to them via the online repos. 
Otherwise the command shown below will give you a source warning and fail:

```
sudo aptitude reinstall '~i'
```

You can instruct your system to reconfigure all installed packages by executing this script:

```
(    for i in `dpkg -l | grep '^ii' | awk '{print $2}'`; do
        echo $i; sudo dpkg-reconfigure $i;
    done
) 2>&1 | tee dpkg-reconfigure.log
```

---

