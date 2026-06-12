---
title: "Disable User List in GDM"
date: 2014-10-15
forum: General Help
---

### Post by Dave_Ryan on 2014-10-15
I need to remove the user list from the GDM login screen.

I have researched this everywhere including this forum. I can only find results for other versions of Ubuntu.
Those suggestions helped me locate the files I need to change, but they do not work.

I currently have Ubuntu 14.04 installed:

Distributor ID: Ubuntu
Description:    Ubuntu 14.04.1 LTS
Release:        14.04
Codename:       trusty

-----------------------------------
I have the latest version of GDM for trusty:

ii  gdm                                        3.10.0.1-0ubuntu3                          i386         Next generation GNOME Display Manager
ii  gir1.2-gdm-1.0                          3.10.0.1-0ubuntu3                          i386         GObject introspection data for the GNOME Display Manager
ii  libgdm1                                   3.10.0.1-0ubuntu3                          i386         Next generation GNOME Display Manager (shared libraries)

-----------------------------------
I have set the key in org.gnome.login-screen.gschema.xml to not list the users:

/usr/share/glib-2.0/schemas/org.gnome.login-screen.gschema.xml
    <key type="b" name="disable-user-list">
      <default>true</default>
      <summary>Avoid showing user list</summary>
      <description>The login screen normally shows a list of available users to log in as. This setting can be toggled to disable showing the user list.</description>
    </key>

-----------------------------------
I even set it in the greeter.gsettings file:

/etc/gdm/greeter.gsettings
# - Disable user list
disable-user-list=true

-----------------------------------
I have even placed these settings in the /etc/gdm/custom.conf file.

-----------------------------------
I reviewed the /etc/init.d/gdm script and file default-display-manager has gdm as the display manager:

/etc/X11/default-display-manager
/usr/sbin/gdm

-----------------------------------
So how in Ubuntu 14.04 with 3.10.0.1-0ubuntu3 do I disable the login screen from displaying the usernames. I want them to put in the usersname and password each time.

If I need to switch to lightdm, How to I accomplish the same thing, plus how do I force the same background and remove the "dots".

Any assistance would be helpful. 

Dave Ryan
Wednesday, October 15, 2014 1452 hrs MDT

---

