---
title: "How run flatpak files ?"
date: 2024-11-10
forum: General Help
---

### Post by aug7744 on 2024-11-10
Hello. Thanks for reading my topic. I see an Hanbrake version in flatpak file format. How works the flatpak format ? Is same as appimage ? Need run any command before to run ? If need run an command what process will be done ? Internet access to download extra flatpak files ? Is possible run flatpak file format in an offline system without internet access having only flatpak software installed ?  Have an nice week.

---

### Post by Dennis N on 2024-11-10
You first have to set up Flatpak support in Ubuntu. See directions [here]("https://flathub.org/"): Click on "Set Up Flathub". You can also search for apps on that page at the top. 

For Handbrake, you will see the Handbrake page with an Install button. 

With Ubuntu, once the app is installed, you click on it's icon in Ubuntu's "Show Apps" display to launch the program. Or you can search for it in the Applications Overview and launch from there.

If  you have Lubuntu, I would guess that it will show up in your applications menu. I don't use Lubuntu, so can't be sure.

---

### Post by grahammechanical on 2024-11-10
Flatpak applications can be installed in Ubuntu but not through the App Centre or from Ubuntu repositories. Flatpak is not Canonical software. 

[https://flatpak.org/](https://flatpak.org/)

Flatpak is definitely not the same as AppImage. It has a closer similarity to Snap packaging than AppImage. Both Flatpak and Snap applications run confined by default. AppImage applications do not run confined by default but can be set up to be confined.

[https://appimage.org/](https://appimage.org/)

[https://snapcraft.io/](https://snapcraft.io/)

How to install FlatPak on Ubuntu

[https://flatpak.org/setup/Ubuntu](https://flatpak.org/setup/Ubuntu)

Regards

---

### Post by joepesci2 on 2024-11-10
> **Dennis N said:**
> You first have to set up Flatpak support in Ubuntu. See directions [here]("https://flathub.org/"): Click on "Set Up Flathub". You can also search for apps on that page at the top. 

For Handbrake, you will see the Handbrake page with an Install button. 

With Ubuntu, once the app is installed, you click on it's icon in Ubuntu's "Show Apps" display to launch the program. Or you can search for it in the Applications Overview and launch from there.

If  you have Lubuntu, I would guess that it will show up in your applications menu. I don't use Lubuntu, so can be sure.

> **grahammechanical said:**
> Flatpak applications can be installed in Ubuntu but not through the App Centre or from Ubuntu repositories. Flatpak is not Canonical software. 

[https://flatpak.org/](https://flatpak.org/)

Flatpak is definitely not the same as AppImage. It has a closer similarity to Snap packaging than AppImage. Both Flatpak and Snap applications run confined by default. AppImage applications do not run confined by default but can be set up to be confined.

[https://appimage.org/](https://appimage.org/)

[https://snapcraft.io/](https://snapcraft.io/)

How to install FlatPak on Ubuntu

[https://flatpak.org/setup/Ubuntu](https://flatpak.org/setup/Ubuntu)

Regards

Good afternoon, im going to take advantage of this thread to raise a question regarding Flatpak.

Who is in charge of maintaining the repository of the programs in Flatpak?
Is each owner/developer responsible for its maintenance and security?

For example:
[https://flathub.org/apps/org.mozilla.firefox](https://flathub.org/apps/org.mozilla.firefox)

Here we have Firefox in Flatpak, is Mozilla in charge of keeping this repository updated and that it does not contain anything malicious?

Thank you very much for your time and help.

---

### Post by Dennis N on 2024-11-10
The developer is responsible for maintaining his/her package. On Flathub, applications with the check mark by their name are verified to come from the developer, not some bad actor. See image. The Firefox flatpak is packaged by Mozilla. Its a good alternative to the snap and offers more flexibility as to file system access.

See this:
[https://docs.flathub.org/docs/for-users/verification/](https://docs.flathub.org/docs/for-users/verification/)

---

### Post by joepesci2 on 2024-11-10
> **Dennis N said:**
> The developer is responsible for maintaining his/her package. On Flathub, applications with the check mark by their name are verified to come from the developer, not some bad actor. See image. The Firefox flatpak is packaged by Mozilla. Its a good alternative to the snap and offers more flexibility as to file system access.

See this:
[https://docs.flathub.org/docs/for-users/verification/](https://docs.flathub.org/docs/for-users/verification/)

Great, thanks a lot.
So i understand that verified apps are 100% safe and can be trusted without any problem, right?

As you say, it seems like a good alternative to installing Firefox, since Ubuntu requires you to install it via Snap.

Thanks a lot for your help.

---

### Post by aug7744 on 2024-11-10
Thanks for all replies !
 I have downloaded an file for test HandBrake-1.5.1-x86_64.flatpak
 after was done an command flatpak install --bundle HandBrake-1.5.1-x86_64.flatpak
  Thus was showed some details about need download dependencies and 2 warnings

  Info: runtime org.gnome.Platform branch 41 is end-of-life, with reason:    The GNOME 41 runtime is no longer supported as of September 17, 2022. Please ask your application developer to migrate to a supported platform. 
Info: applications using this runtime:    fr.handbrake.ghb  Info: runtime org.freedesktop.Platform.GL.default branch 21.08 is end-of-life, with reason:    org.freedesktop.Platform 21.08 is no longer receiving fixes and security updates. Please update to a supported runtime version. Info: applications using this runtime:    fr.handbrake.ghb   I not understand if because the host OS not is or not GNOME 41 and use runtime org.freedesktop.Platform.GL.default old version.  

After was showed the dependencies and total size to download ... BIG EVEN for an software that installing by deb file is less of 50 MB  

1.     org.freedesktop.Platform.GL.default                       21.08              i              flathub                < 129,8 MB  
2.     org.freedesktop.Platform.GL.nvidia-470-256-02             1.4                i              flathub                < 273,8 MB  
3.org.freedesktop.Platform.openh264                         2.0                i              flathub                  < 1,5 MB  
4.     org.gnome.Platform.Locale                                 41                 i              flathub                < 337,1 MB (partial)  
5.     org.gtk.Gtk3theme.Arc-Darker                              3.22               i              flathub                < 140,3 kB  
6.     org.gnome.Platform                                        41                 i              flathub                < 292,7 MB  
7.     fr.handbrake.ghb                                          stable             i              ghb-origin             0 bytes   

ALL ABOVE ONLY TO INSTALL HANDBRAKE ... 
Perhaps others software will need more dependencies. Perhaps Flatpak does less or not problems if compared with Snaps and has good security too. I need see if is good install Flatpaks ... if each Flatpak require much dependencies I see better continue using apt deb file installation.
 Other detail is here is Lubuntu using LXQT and not GNOME, but reading all above and the warning information is as require GNOME. I need post an topic in Lubuntu forums about it.  

Have an nice week for all users !

---

### Post by grahammechanical on 2024-11-10
> The Firefox flatpak is packaged by Mozilla.

So, that there is no misunderstanding - Mozilla is also the maintainer of the Firefox snap and the Thunderbird snap is maintained by Canonical. The App Centre identifies the maintainer of the snap packaged apps in the App Centre. 

Regards

---

### Post by Dennis N on 2024-11-10
**@aug7444**

Your downloaded file is out of date. Please understand that no downloading is needed to install Flatpaks. You should have followed the directions I gave in post #2 of this thread to set up Flathub and install a Flatpak application. Then you would have gotten the latest version which is 1.8.2.  

You can upgrade to the newest version by running
```
flatpak update
``` 
command. It will upgrade Handbrake and install any newer support files it needs. Then run:
```
flatpak uninstall --unused
```
to remove the older versions of the support files.

The support files that came with your installation (called runtimes) are shared between applications. If you install another application using the same runtime you don't download it a second time. Only one copy is on your computer.

If you followed all the setup instructions for Flathub, you also have Gnome Software installed. You can install Flatpak versions of applications without using the terminal with Gnome Software.

---

### Post by joepesci2 on 2024-11-11
> **Dennis N said:**
> The developer is responsible for maintaining his/her package. On Flathub, applications with the check mark by their name are verified to come from the developer, not some bad actor. See image. The Firefox flatpak is packaged by Mozilla. Its a good alternative to the snap and offers more flexibility as to file system access.

See this:
[https://docs.flathub.org/docs/for-users/verification/](https://docs.flathub.org/docs/for-users/verification/)

> **grahammechanical said:**
> So, that there is no misunderstanding - Mozilla is also the maintainer of the Firefox snap and the Thunderbird snap is maintained by Canonical. The App Centre identifies the maintainer of the snap packaged apps in the App Centre. 

Regards

I understand now.
Programs in Flatpak that have owners ID verified, such as Firefox, OBS, etc., can be assured that they are 100% safe and free of malicious code and that they will also receive the various updates.

This is great and very reassuring.
The problem will come with unverified owners.

Thank you very much for your help.

---

