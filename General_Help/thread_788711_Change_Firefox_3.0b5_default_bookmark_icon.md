---
title: "Change Firefox 3.0b5 default bookmark icon?"
date: 2008-05-10
forum: General Help
---

### Post by BandD on 2008-05-10
Does anyone know how Firefox 3.0b5 chooses the default bookmark icon (i.e. if the site doesn't have its own favicon, ex. [www.rockbox.org]("http://www.rockbox.org"))  

Does it inherit it from the current Icon theme, and if so, what filename does it look for?

For me it is the same as /usr/share/icons/gnome/scalable/mimetypes/html.svg There are many other files within the mimetypes folder with the same image, I just gave that one as an example.  

I've tried renaming all the files in my current icon set to match the names within the /usr.../gnome/ icon set.  But it doesn't change.  I'm wondering if there needs to be a 'gtk' in the file name or something.

Anyway, if anyone has any input I'd greatly appreciate it.

---

### Post by BandD on 2008-05-10
Alternitively, after some poking around...would it be possible to assign a default icon in the boomarks.html document in /home/.mozilla/firefox/CURRENT_PROFILE.

Here is the beginning of my document with a couple bookmarks:

```
<!DOCTYPE NETSCAPE-Bookmark-file-1>
<!-- This is an automatically generated file.
     It will be read and overwritten.
     DO NOT EDIT! -->
<META HTTP-EQUIV="Content-Type" CONTENT="text/html; charset=UTF-8">
<TITLE>Bookmarks</TITLE>
<H1 LAST_MODIFIED="1209198243">Bookmarks</H1>

<DL><p>
    <DT><H3 ADD_DATE="1193810785" LAST_MODIFIED="1193810812" ID="rdf:#$GW5Ok3">Arius Departure</H3>
    <DL><p>
        <DT><A HREF="http://www.maff-aqs.go.jp/english/ryoko/ta.htm" ADD_DATE="1193809986" LAST_VISIT="1193811418" LAST_CHARSET="ISO-2022-JP" ID="rdf:#$HW5Ok3">Bring Animals</A>
        <DT><A HREF="http://japan.usembassy.gov/e/acs/tacs-petse.html" ADD_DATE="1193809995" LAST_VISIT="1193810482" ICON="data:image/x-icon;base64,AAABAAEAEBAQAAAAAAAoAQAAFgAAACgAAAAQAAAAIAAAAAEABAAAAAAAwAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAACAAACAAAAAgIAAgAAAAIAAgACAgAAAgICAAMDAwAAAAP8AAP8AAAD//wD/AAAA/wD/AP//AAD///8AAAAAAAAAAAAAAAAAAAAAAId3d3d3d3d3j/////////eJmZmZmZmZl4/////////3iZmZmZmZmZeM/Pz8////94/Pz8+ZmZmXjPz8/P////ePz8/PmZmZl4z8/Pz////3iIiIiIiIiIgAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAD//wAA//8AAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAAA//8AAP//AAD//wAA" LAST_CHARSET="UTF-8" ID="rdf:#$IW5Ok3">Exporting Pets from Japan</A>
        <DT><A HREF="http://www.maff-aqs.go.jp/english/soshiki/telephonelist_f.htm" ADD_DATE="1193810777" LAST_VISIT="1193811356" LAST_CHARSET="ISO-2022-JP" ID="rdf:#$JW5Ok3">Animal Quarantine Stations</A>
```

I don't really have an html knowledge, so I don't know if this is an option.  But basically the idea would be to specify a default icon (a native path to the icon my one's own choosing) and everytime a bookmarked website doesn't have its own favicon then this specified default icon would be used.  But maybe it's not possible.  Just a work around I thought might work.

---

