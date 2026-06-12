---
title: "Clear recently played in Totem?"
date: 2005-06-29
forum: General Help
---

### Post by Hokputooy on 2005-06-29
I've been searching for a way to clear the list of recently played files under the movie menu in Totem and have found nothing. Does anyone know how?

---

### Post by deadbattery on 2005-06-29
if you clear your recent documents history the Totem history will empty also

/main menu/places/recent documents/clear recent documents

---

### Post by Hokputooy on 2005-06-29
Thanks.

---

### Post by Navin_Johnson on 2005-06-30
hmm.  So just what were you watching that you now want no record of? :razz:  [-X 

-Navin Johnson

---

### Post by Ron O on 2008-03-03
Hi All,

I am using Totem in Xubuntu (XFCE- Gutsy) that does not have a Places-Recent Documents option that I can find. 
I found a way to remove recent documents from Totem that also does not affect the recent documents lists in other applications. It works in Xubuntu- I don't know about Ubuntu(Gnome) or the other dstros.

Path:  /usr/share/totem

With root permissions, save the file  totem-ui.xml  to  totem-ui.xml.bak  in case you need to restore it.

Copy the contents of this file to a new text document that you will save as the new  totem-ui.xml after the following changes. 

Here is the beginning of this XML file. Just delete the two lines I have indicated with ************, including their indents.

<ui>
	<menubar name="tmw-menubar">
		<menu name="movie" action="movie-menu">
			<menuitem name="open" action="open"/>
			<menuitem name="open-location" action="open-location"/>
			<placeholder name="devices-placeholder"/>
			<separator name="recent-separator"/>	****************************
			<placeholder name="recent-placeholder"/>  **************************
			<separator/>
			<menuitem name="properties" action="properties"/>
			<separator/

Now save it as  totem-ui.xml. At first, I thought this might cause a problem when the system tries to drop the recent variables into a missing placeholder, but it seems to work fine. 

 .

---

