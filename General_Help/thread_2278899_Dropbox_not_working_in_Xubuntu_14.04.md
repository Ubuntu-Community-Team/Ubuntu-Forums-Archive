---
title: "Dropbox not working in Xubuntu 14.04"
date: 2015-05-19
forum: General Help
---

### Post by tessk2 on 2015-05-19
Been having a lot of issues with this. It used to work before, then I re-installed the OS, now it is not working at all. 

I downloaded the 64 bit .deb file from the website, ran it, it downloaded some software, then gave me a message about needing a daemon and quit. 

I had the Application menu Dropbox entry, but selecting it did nothing. I restarted a couple times, still nothing. Dropbox does not autostart, and if you enter
    
    dropbox status

in the terminal it says it is not running. You cannot get it to start either, it says
    
    $ dropbox start  
    Dropbox isn't running!
    Dropbox is already running!

I tried uninstalling & reinstalling, no dice. I tried installing the nautilus-dropbox from apt-get, that installed something but it still did nothing. Restarting in between every attempt, btw. I did more stuff, tried installing through synaptic, I uninstalled it again & ran everything in here:

[http://iasptk.com/ubuntu-fix-broken-package-best-solution/](http://iasptk.com/ubuntu-fix-broken-package-best-solution/)

and in here:

[http://ubuntuforums.org/showthread.php?t=2217639](http://ubuntuforums.org/showthread.php?t=2217639)

and I did everything in here too:

[http://ubuntuforums.org/showthread.php?t=2196760](http://ubuntuforums.org/showthread.php?t=2196760)

and also everything in here:

[http://www.webupd8.org/2012/08/how-to-install-dropbox-in-xubuntu-and.html](http://www.webupd8.org/2012/08/how-to-install-dropbox-in-xubuntu-and.html)

None of it worked or made a difference. 

I opened up my ** /var/lib/dpkg/status** as described here but could not find anything broken, not that I even knew what a broken package would look like:
[http://iasptk.com/ubuntu-fix-broken-package-best-solution/](http://iasptk.com/ubuntu-fix-broken-package-best-solution/)

So after all that, I am back where I started; I have Dropbox showing up in my Application menu, but its not running. When I click on the Application menu entry, nothing happens. I don't have a Dropbox or .dropbox folder in my home directory, and I can't start or stop the program on the command line. I even went in the Session & Startup settings and there is no entry for it in there. 

Any ideas? Thanks.

---

### Post by Kurt_Alan on 2015-05-21
When you say Dropbox is not working, I'm not sure what "it" refers to. For me, the Dropbox indicator has failed since some time late 2014, for Xubuntu, which means that you cannot access menu preferences including the powerful "selective sync" feature.

But dropbox has installed correctly and it functions passively and correctly. You can access it via CLI "dropbox status."

This is  the latest information that I have received from dropbox.com technical support. Hopefully, you can find some things here that will be helpful.

If you get it running but there is no indicator please let me know, as I am trying to resolve this problem via the dependencies necessary to run Qt 5.3 which Dropbox now requires. You will see the dependencies listed below. I have not been able to either find (all of them) or satisfy them properly.

The question of the indicator fail aside, you will also find here directions for a thorough uninstall and reinstall.  One item missing from these directions is the necessity of nautilus-dropbox (Synaptic). Without this, you have no CLI access.

The first set of information below is from first level dropbox support, the second, re: compatibility issues with Xubuntu is from escalated support:

NUMBER ONE:

Harley, May 7, 8:49 PM:
Hi Kurt!
Thanks for writing in. My name is Harley, and I'd be happy to assist you with this.
When new versions of the Dropbox desktop application are released, issues can arise on computers that use Linux because of the difficulty of testing the latest version on all of the distributions of Linux that exist.
For your computer with Xubuntu 14.04, I'm going to give you the steps to perform a complete uninstall of Dropbox, then install the latest stable release of our software. Hopefully this gives you full functionality again, but if you're still only able to access Dropbox through the command line then we have directions on how to manage selective sync settings in a headless environment here:[https://www.dropbox.com/en/](https://www.dropbox.com/en/).
First, make sure you save and quit ALL programs that access files in the Dropbox folder.
Depending on your OS and the package you used to perform the installation, you could have files in two different locations. I'm sending you instructions for both of the cases, so if some of the commands error out don't worry.
Run the following commands in your terminal:
&#8194;&#8194;&#8194;&#8194; dropbox stop
&#8194;&#8194;&#8194;&#8194; dropbox status&#8194;&#8194;# Should report "not running"
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox-dist
&#8194;&#8194;&#8194;&#8194; rm -rf /var/lib/dropbox
&#8194;&#8194;&#8194;&#8194; rm -rf ~/.dropbox*
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove nautilus-dropbox
&#8194;&#8194;&#8194;&#8194; sudo apt-get remove dropbox
&#8194;&#8194;&#8194;&#8194; rm /etc/apt/source.d/dropbox
After this, you can download version 3.4.6 of Dropbox at your command prompt. Depending on your system, you'll need either the 32-bit or 64-bit installer files.
32-bit installer:
cd ~ && wget -O - "https://d1ilhw0800yew8." | tar xzf -
64-bit installer:
cd ~ && wget -O - "https://d1ilhw0800yew8." | tar xzf -
Next, run the Dropbox daemon from the newly created .dropbox-dist folder to install the application:
~/.dropbox-dist/dropboxd
More installation and CLI information is also available here:
&#8194;&#8194;*[https://www.dropbox.com/](https://www.dropbox.com/)
After doing this, you should have a working version of Dropbox on your Linux system. But if this installation of Dropbox did not resolve your issue, please let me know so we can continue troubleshooting.
I hope this helps!
Have a wonderful day!
Harley


NUMBER TWO

Frida, May 12, 2:21 PM:
Hi Kurt,
My colleague Harley escalated your request to me and I will be assisting you moving forward. My name is Frida and I'm a member of our team who specializes in desktop application issues.
After reviewing the issue you described, it appears that your specific desktop environment of Linux may not be supported by our desktop application. Xubuntu may be supported but you have to make sure that certain dependencies are installed. Please review the "For Advanced Users" section at the bottom of this article for detailed information about this:
[https://www.dropbox.com/en/](https://www.dropbox.com/en/)
You need to make sure that the dependencies are also updated along with the Dropbox desktop application - if you're unsure about this, please reach out to Xubuntu support directly.
I hope this is helpful - please let me know if you have any other questions.
Regards,
Frida


For our advanced users
Linux installer
Dropbox supports the following desktop environments:
Ubuntu (Unity) and GNOME Classic, full support using the package in our*installation page.
XFCE is supported if the corresponding Nautilus dependencies are installed.
GNOME shell natively displays the file overlays, but requires the extension TopIcons to get the application indicator (tray icon).
Dropbox uses*QT 5.3, and as such needs the following software to work on desktop environments:
GTK 2.12 or higher
GLib 2.22 or higher
Libnotify 0.4.4 or higher
Libappindicator 1.0
Nautilus 2.30.0 or higher
The Nautilus installer source code has been released under an MIT license, and people have reported building from source on different versions of Gentoo, Arch Linux, OpenSUSE, and Debian. Your results may vary.

---

