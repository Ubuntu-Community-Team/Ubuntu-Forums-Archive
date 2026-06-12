---
title: "Black screen on boot to console login"
date: 2024-04-14
forum: General Help
---

### Post by Frederico_Zenozzog on 2024-04-14
Hi
I'm using a pared back Ubuntu installation (64bit) to drive an old HP-Proliant NL40 Microserver that is used as a basic file server. The hardware has very limited graphics so nomodeset is a fixture. It mostly runs headless so Grub is also configured to boot to a console login ([link]("https://askubuntu.com/questions/859630/ddg#859637")) -for most maintenance tasks I remote access with SSH.

However, if I attach a monitor,  on a normal boot it goes to a black screen with no cursor. Frustrating....  

As a work around,  I can invoke grub menu > recovery mode  > resume on boot and the system will go to & display the log in prompt screen.

Any ideas on what I should check to try and get the login to display on a normal boot sequence?

Thanks

---

### Post by MAFoElffen on 2024-04-14
As described, you already answered your own question. Let me explain, so you see it...

If you boot to recovery mode and continue... On the way, at boot in that mode, it adds the kernel boot parameter "nomodeset".

If you edit file /etc/default/grub, you could do the same persistently, by going to the GRUB_CMDLINE_LINUX_DEFAULT variable and add either "-- nomodeset" or "-- 3"... which the later will boot it as rcinit 3 or commonly referred as multi-user console mode.

Another way would be to set 
```

GRUB_TERMINAL=console
GRUB_GFX_MODE=1024x768x16

```
Me? Server still uses a VGA graphics mode for its video. As a default, there is still a basic, rudimentary video mode for the vtty consoles. It is not purely text mode, unless you tell it to be. I like to play with my VGA palletes, and how things display on it. Many of my past pure server hardware, I had set a video= setting for it to work with my in-rack server console, which did not have an EDID. I had to use the GRUB commandline and use videoinfo to find the resultion it was happy with, then use (for example "video=1024x768x16"as a boot parameter.

---

### Post by Frederico_Zenozzog on 2024-04-14
Thanks for the response.

As mentioned in my first post I already have grub reconfigured with 

```

GRUB_CMDLINE_LINUX_DEFAULT="text"
GRUB_TERMINAL=console
```
  After making the changes I run:

  ```
sudo update-grub
sudo systemctl enable multi-user.target --force
sudo systemctl set-default multi-user.target

```
Regarding

> Another way would be to set 
```

GRUB_TERMINAL=console
GRUB_GFX_MODE=1024x768x16

```

... I had already tried similar variations on GRUB_GFX_MODE, but as best as i can work out the NL40 will always come up at 640. Maybe that's a hardware limitation. 

I think I'll let sleeping dogs lie and put up with the black screen behaviour. 
 
Cheers

---

### Post by MAFoElffen on 2024-04-15
Be careful that when you read things off the internet, that you check the dates... 
> **Frederico_Zenozzog said:**
> 
...
As mentioned in my first post I already have grub reconfigured with 
```

GRUB_CMDLINE_LINUX_DEFAULT="[COLOR=#ff0000]text[/COLOR]"

```

 "text" has not worked as a kernel boot parameter for console since around or before 2012. That is about the time I joined the Ubuntu Server Team (2012). Even then it wasn't consistent across all Linux distro's..
RE: [https://askubuntu.com/a/710298/138255](https://askubuntu.com/a/710298/138255)

I know, I reported it as not working any more way back over a decade ago. And verified that it can be done as I have noted above: use Kernel parameter "3" in it's place. Yes, I've been around a while. I can interrupt the Grub Menu, edit/add "-- 3" in place of "quiet splash" o a desktop, without anything else (not even the any changes to the unit/target files), and a graphical install will boot as text console. You don't need to believe me, just try it yourself to see.

As for the max resolution of the HP NL40 Microserver, according to the [HP ProLiant Microserver NL40L Owners Manual Thread "part 3"]("https://www.avforums.com/threads/hp-proliant-microserver-n40l-owners-thread-part-3.1636476/page-21"), on page 21... max res is 1920x1080. 

Like I said... But it depends with what it is connected to. To confirm the combination with a display you have connected, at the Grub Boot Menu > Press the <C> key to drop to a Grub prompt > if Legacy BIOS, "vbeinfo", else if EFI BIOS, then "videoinfo"...

---

