---
title: "Video problems after automatic update"
date: 2008-01-27
forum: General Help
---

### Post by Vind on 2008-01-27
Hello everyone.

About a couple of weeks ago, after allowing an automatic update, I had a problem with my video settings. When booted the PC would load ok up to the login screen, once there and after entering login information, the computer would freeze when trying to start the desktop up and it would suddenly go back to the login screen. Talking to a more experienced friend he told me to modify my graphic settings back to default using the following command:

> sudo dpkg-reconfigure -phigh xserver-xorg

After using this comand my pc was able to start up without any problems. My question is, what must i do in order to get my PC back to how it was running with the graphics card driver?

I use an Nvidia 7600 graphics card and had the latest Linux-32 bit Nvidia driver installed. Must I uninstall the previous installation of the driver? and if so, how do i go about it? Can i just make an installation over the previous installation?

Thank you in advance for your time.

---

### Post by lebiathan on 2008-01-27
In a terminal you can type 
```
sudo displayconfig-gtk
```

and give your root password. Alternatively, you may do this using the UI via

System -> System Management -> Screens and Graphics

and type your root password. There you will find options about configuring your screen graphics. In case after a reboot problems like the previous ones you had continue to exist, you should retype the command your friend told you and reboot (which will work ok then).

If the problem persists, it is most likely that the configuration that you have given is not supported by your graphic cards (despite the fact that it might be present as an option).

George

---

### Post by Vind on 2008-01-27
Thank you for the quick reply.

I was aware of how to access my graphic settings in that way, but it does not help in solving the matter. After running the command posted in the original post, the xorg file seems to have been replaced by a default one which has allowed me to enter the operating system once again but in some way has disabled the Nvidia driver. I need this operating in order for my window borders to be visible and for compiz fusion to work. When trying to change the settings through the Nvidia interface i get the following message:

> You do not appear to be using the NVIDIA X driver. Please edit your xconfiguration file (just run 'nvidia-xconfig' as root), and restart x server

If i do as told,  when I try to log in i get back to having the problem once again. That is: not being able to get past the login screen. I assume this is because I am enabling the file that was giving me the problems in the first place. My guess is that something in the configuration (after the update) is giving me the problems so perhaps a possible solution is the modification of the config file or to make a new installation of the Nvidia driver.

I would like to comment on the fact that my configuration was working perfectly until the last automatic update.

All help is appreciated and thank u again for your time.

---

### Post by Vind on 2008-01-29
Hi again.

The problem is solved. I was given a guide on how to totally remove an Nvidia driver from the computer and made a fresh reinstallation keeping the settings on the default xorg file created by the comand posted on the first post. That has done the trick. Unfortunately i do not have link to the guide since it was given to me in paper format.

Vind

---

