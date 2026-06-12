---
title: "Unable to change login background."
date: 2014-10-26
forum: General Help
---

### Post by rusty7600 on 2014-10-26
I am using Ubuntu 14.04. I tried changing the login background, but all it shows me is whatever background color I chose. I have the background I want in /usr/share/backgrounds/ in .jpg format. I tried png but that didn't work either. I also tried changing permissions to the folder. Still nothing. I tried using dconf and Ubuntu tweak, but I also tried manually editing the files located in /usr/share/glib-2.0/schemas/, and the same thing is still happening. It will change the lock screen to the wallpaper I select, but not the initial login screen. Most other parameters I've tried have worked, except for the wallpaper.

Thank's

---

### Post by Paulgirardin on 2014-10-26
Install GRUB customiser.This allows the login wallpaper to be set to your preference.  

[http://ubuntuforums.org/showthread.php?t=1664134](http://ubuntuforums.org/showthread.php?t=1664134)

---

### Post by papibe on 2014-10-26
Hi rusty7600.

Are you trying to set a pre installed background, or is it a custom one?

If it is a custom, downloaded, or created by you, try coping it into your Pictures folders, and then select it using 'Appearance'.

Does that make a difference?

let us know how it goes.
Regards.

---

### Post by rusty7600 on 2014-10-26
How would a GRUB customizer let me change my Ubuntu login screen? I have it installed, but i'm not seeing any options for the actual Ubuntu login.

To Papibe, I'm not completely sure what you mean. I know how to change my desktop wallpaper, I'm trying to change my login wallpaper. Unless changing the desktop wallpaper has some effect on it that i'm not aware of.

---

### Post by papibe on 2014-10-26
The login wallpaper is, or should be, the same as the desktop wallpaper.

Do you want them to be different?

Regards.

---

### Post by rusty7600 on 2014-10-26
It wasn't the same when I installed. As a default configuration it doesn't make sense. I don't think I've ever seen an OS, windows or linux, where the login screen is the exact same as the user account wallpaper. Lock screen, maybe, but not for the actual login screen. I can configure the lock screen. What I'm trying to configure is the login screen.

---

### Post by Paulgirardin on 2014-10-26
If you set a custom background image it carries over into the login screen.
It does on my system,anyway.

---

### Post by rusty7600 on 2014-10-26
So you just go to system settings >> Appearance, set your wallpaper, and it's automatically saved as your login as well?

---

### Post by grahammechanical on 2014-10-26
The default background image is called warty-final-ubuntu.png. If we choose to have the desktop wallpaper image as a slide show, then the login screen background image is warty-final-ubuntu.png. If we choose a static wallpaper then that image becomes comes the background image for the login screen.

If we want other images to be used as a wallpaper then we can put the image in the Pictures folder and in the Appearance utility we click the little down arrow in the panel that says wallpapers and we change it to Pictures. Then we can select our own images as wallpaper and that image may become the background image for the login screen. I cannot say it will happen for sure because I have never tried it. But there is another way and I have not messed with this for more than two years. So, who knows if it will work.

We put our image in /usr/share/backgrounds as you have done but it does not appear as a background image. Does it? So we go to /usr/share/gnome-background-properties and we edit trusty-wallpapers.xml. We can do it with Gedit but we need administrative privileges to edit this file. This is an example of the markup

>   <wallpaper>
    <name>Forever</name>
    <filename>/usr/share/backgrounds/Forever_by_Shady_S.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>

We add a new section like this

>   <wallpaper>
    <name>OurNameImage</name>
    <filename>/usr/share/backgrounds/OurNameImage.jpg</filename>
    <options>zoom</options>
    <pcolor>#000000</pcolor>
    <scolor>#000000</scolor>
    <shade_type>solid</shade_type>
  </wallpaper>




Now, our chosen image will show up as a background wallpaper that we can select and it should also become the background image of the login screen. There is one little problem. Gedit will create a backup of the file and will add a tilde ( ~ ) character to the beginning of the file name. The file will then become a hidden file but it will still be read by Ubuntu and that can cause complications. It needs to be deleted.

I experimented with all this more than two years ago. I even worked out how to create my own background image slide show. I cannot say for sure if this method still works.

Regards.

---

### Post by papibe on 2014-10-26
> **rusty7600 said:**
> So you just go to system settings >> Appearance, set your wallpaper, and it's automatically saved as your login as well?
That's the default behavior. Also the default is that the login screen background is the same as lock screen backgound.

Regards.

---

### Post by deadflowr on 2014-10-26
> **grahammechanical said:**
> 
Now, our chosen image will show up as a background wallpaper that we can select and it should also become the background image of the login screen. There is one little problem. Gedit will create a backup of the file and will add a tilde ( ~ ) character to the beginning of the file name. The file will then become a hidden file but it will still be read by Ubuntu and that can cause complications. It needs to be deleted.
or rather it adds the images named in the backup so yeah, it adds confusion by listing a bunch of duplicate entries.

> I experimented with all this more than two years ago. I even worked out how to create my own background image slide show. I cannot say for sure if this method still works.
It still does.
You can even use the base of the file and create a separate file from it if you want.
As long as it goes into the folder mentioned(/usr/share/gnome-background-properties)

But on topic, OP what did you set the permissions for the file?
If the file is set for Others to read, then it should show.

---

