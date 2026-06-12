---
title: "recovery the wine menu on K menu ?"
date: 2008-06-27
forum: General Help
---

### Post by firsttimeuser on 2008-06-27
Hi guys, I deleted the wine menu on the K menu by accident and I really want it back.

The wine on the K menu used to list all the installed applications under its submenu, is it possible I recovery this?

:confused::confused::confused:

---

### Post by mc4man on 2008-06-27
See here
[http://ubuntuforums.org/showthread.php?t=650738](http://ubuntuforums.org/showthread.php?t=650738)

Edit : that may not work in hardy - gonna test

The location has changed and this is on _ubuntu hardy_ (may be different on kubuntu)
It's in /home/username/.config/menus - applications.menu
Sometimes editing that menu will cause the applications drop down to disappear, if so delete it (applications.menu) and reboot. i was just able to restore some deleted categories like this
```
<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>Other</Name>
		<Include>
			<Filename>displayconfig-gtk.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>Accessories</Name>
		<Include>
			<Filename>nautilus.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
	</Menu>
	<Menu>
		<Name>Universal Access</Name>
		<DirectoryDir>/home/doug/.local/share/desktop-directories</DirectoryDir>
		<Deleted/>   [COLOR="Red"]<-  removed[/COLOR]
	</Menu>
	<Menu>
		<Name>Development</Name>
		<Include>
			<Filename>bug-buddy.desktop</Filename>
		</Include>
		<AppDir>/home/doug/.local/share/applications</AppDir>
		<Deleted/>  [COLOR="Red"]<- removed[/COLOR]
	</Menu>
</Menu>
```

Appears to be same idea on kubuntu 
home/.config/menus/applications-kmenuedit... just remove the <Deleted/> if found, nothing else.

---

### Post by firsttimeuser on 2008-06-27
Thanks mc4man.

Yes, removing the <delete> does bring back the wine and all its submenus, but somehow under the program submenu it does not have the programs I already installed. I tried to uninstall and reinstall wine, and then installed the application(foxit), still no help, nothing under the program submenu besides the notepad.

Odd

---

### Post by mc4man on 2008-06-27
What you might want to try is uninstall wine once again, then go to home dir. and delete the .wine dir. Then go home/.config/menus/applications-merged and delete the wine programs file. then go home/.local/share/applications/ and delete the wine folder.
Haven't had a chance to test should be safe.
You could also go home/.local/share/desktop-directories and if there is a _folder for the program in question _then delete it. I wouldn't delete the wine-Programs.directory, at least till i can try it. (don't mind borking this install)

You should refrain from deleting categories and apps from the main menu, unchecking is fine, deleting can be hard to undo.

---

