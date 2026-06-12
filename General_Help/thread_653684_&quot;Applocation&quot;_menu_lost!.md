---
title: "&quot;Applocation&quot; menu lost!"
date: 2007-12-30
forum: General Help
---

### Post by maysam on 2007-12-30
Hi 
I was editing "Main Menu" but after that "Application" menu disappear into a small dot; I read other thread, but no luck!

---

### Post by chewearn on 2007-12-30
Try deleting the entire menu applet, and add a new one?

---

### Post by maysam on 2007-12-30
Thanks for reply. But i found the solution:
[I've Gutsy]
Open** /home/[username]/.config/menus/applications.menu**
Replace the content by:

[B]<!DOCTYPE Menu
  PUBLIC '-//freedesktop//DTD Menu 1.0//EN'
  'http://standards.freedesktop.org/menu-spec/menu-1.0.dtd'>
<Menu>
	<Name>Applications</Name>
	<MergeFile type="parent">/etc/xdg/menus/applications.menu</MergeFile>
	<Menu>
		<Name>Other</Name>
		<DirectoryDir>/home/lomion/.local/share/desktop-directories</DirectoryDir>
	</Menu>
	<Menu>
		<Name>Development</Name>
		<DirectoryDir>/home/lomion/.local/share/desktop-directories</DirectoryDir>
		<Include>
			<Filename>python2.5.desktop</Filename>
		</Include>
		<AppDir>/home/lomion/.local/share/applications</AppDir>
		<Include>
			<Filename>alacarte-made.desktop</Filename>
		</Include>
	</Menu>
	<Menu>
		<Name>System</Name>
		<Include>
			<Filename>gconf-editor.desktop</Filename>
		</Include>
		<AppDir>/home/lomion/.local/share/applications</AppDir>
	</Menu>
</Menu>[/B]

:guitar:

---

