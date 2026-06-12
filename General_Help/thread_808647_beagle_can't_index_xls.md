---
title: "beagle can't index xls"
date: 2008-05-26
forum: General Help
---

### Post by jasonkwok on 2008-05-26
Hi,
  I'm using Hardy by Wubi. I created some very simple .xls, .doc, and .ods files with openoffice (and ms office too). I found beagle can index and search on all other formats (that I mentioned), but .xls. I think excel files has long been supported by beagle, right?

---

### Post by dbera on 2008-05-27
> **jasonkwok said:**
> Hi,
  I'm using Hardy by Wubi. I created some very simple .xls, .doc, and .ods files with openoffice (and ms office too). I found beagle can index and search on all other formats (that I mentioned), but .xls. I think excel files has long been supported by beagle, right?

You need the package which contains the program ssindex. Ask in the ubuntu irc forums about this.

---

### Post by jasonkwok on 2008-05-30
Hi,
  Thanks for your nice reply. Yes, I found the ssindex in Gnumeric packages. After installing it, beagle still can't find what I needed. Then I look into the "backends" and "Gnumeric" was not there. Does it mean the support of Gnumeric (or excel) was not included in official version of beagle in Ubuntu? But it can find other office files and open office files fine!:???:

Jason

---

### Post by dbera on 2008-05-30
> **jasonkwok said:**
> Hi,
  Thanks for your nice reply. Yes, I found the ssindex in Gnumeric packages. After installing it, beagle still can't find what I needed. Then I look into the "backends" and "Gnumeric" was not there. Does it mean the support of Gnumeric (or excel) was not included in official version of beagle in Ubuntu? But it can find other office files and open office files fine!:???:

Jason

AFAIK, ssindex is a runtime dependency i.e. as long as it is indexed, xls files will be indexed. You can do one test. Find an xls file and then from a terminal,

$ beagle-extract-content /path/to/some/file.xls

See what it reports. If everything is all right, then you will see some properties and the text data as output.

---

### Post by jasonkwok on 2008-06-01
Thank you again. Below is the output :

jason@jason-desktop:~$ beagle-extract-content /home/jason/Documents/test2.xls
Filename: file:///home/jason/Documents/test2.xls
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
Debug: Loaded 60 filters from /usr/lib/beagle/Filters/Filters.dll
Debug: Verifying filter_cache at /home/jason/.beagle/filterver.dat ... cache is dirty ? False
Filter: Beagle.Filters.FilterSpreadsheet (determined in .18s)
MimeType: application/vnd.ms-excel

Properties:
  Timestamp = 2008-05-30 15:41:31 (Utc)
  beagle:FileType = document

Debug: Exception occurred while indexing /home/jason/Documents/test2.xls.
Debug: System.Xml.XmlException: Multiple document element was detected.  Line 2, position 4.
  at Mono.Xml2.XmlTextReader.ReadStartTag () [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at Beagle.Filters.FilterSpreadsheet.WalkContentNodes (System.Xml.XmlReader reader) [0x00000] 
  at Beagle.Filters.FilterSpreadsheet.DoPull () [0x00000] 
Content:
Sheet1



Text extracted in .36s


======
It still can't searched by beagle.

---

### Post by dbera on 2008-06-01
> **jasonkwok said:**
> Thank you again. Below is the output :

jason@jason-desktop:~$ beagle-extract-content /home/jason/Documents/test2.xls
Filename: file:///home/jason/Documents/test2.xls
Debug: Done reading conf from /etc/beagle/config-files/Daemon.xml
Debug: Loaded 60 filters from /usr/lib/beagle/Filters/Filters.dll
Debug: Verifying filter_cache at /home/jason/.beagle/filterver.dat ... cache is dirty ? False
Filter: Beagle.Filters.FilterSpreadsheet (determined in .18s)
MimeType: application/vnd.ms-excel

Properties:
  Timestamp = 2008-05-30 15:41:31 (Utc)
  beagle:FileType = document

Debug: Exception occurred while indexing /home/jason/Documents/test2.xls.
Debug: System.Xml.XmlException: Multiple document element was detected.  Line 2, position 4.
  at Mono.Xml2.XmlTextReader.ReadStartTag () [0x00000] 
  at Mono.Xml2.XmlTextReader.ReadContent () [0x00000] 
  at Mono.Xml2.XmlTextReader.Read () [0x00000] 
  at System.Xml.XmlTextReader.Read () [0x00000] 
  at Beagle.Filters.FilterSpreadsheet.WalkContentNodes (System.Xml.XmlReader reader) [0x00000] 
  at Beagle.Filters.FilterSpreadsheet.DoPull () [0x00000] 
Content:
Sheet1



Text extracted in .36s


======
It still can't searched by beagle.

Yes, the above *"Debug: Exception occurred while indexing ... System.Xml.XmlException: Multiple document element was detected.  Line 2, position 4."* just means beagle is not able to recognize the format of the xls file. Does this happen for any xls file ? Or for some files. Which application did you use to generate the xls files ? Can you take a very small xls file and attach the output of "ssindex -i <filename.xls>" ?

It could be a bug in ssindex or beagle or maybe the application generating the xls file. You should file a bug for Ubuntu or beagle (in [http://bugzilla.gnome.org/](http://bugzilla.gnome.org/)    product=beagle).

---

### Post by jasonkwok on 2008-06-02
ssindex do it correctly, but not beagle. Problem is how can I make beagle to work with ssindex. Is it configuration or compile time (I use official package) problem?

Output of ssindex -i test2.xls :

Reading file:///home/jason/Documents/test2.xls
Excel 97 +
<?xml version="1.0" encoding="UTF-8"?>
<gnumeric>
  <data>Sheet1</data>
  <data>Jason Kwok</data>
  <data>Agnes</data>
  <data>jason</data>
  <data>Sheet2</data>
  <data>Sheet3</data>
</gnumeric>

---

### Post by dbera on 2008-06-02
> **jasonkwok said:**
> ssindex do it correctly, but not beagle. Problem is how can I make beagle to work with ssindex. Is it configuration or compile time (I use official package) problem?

Its not your fault. Apparently ssindex changed its output a long time back, but beagle code was not changed and no one even pointed it out before!

[http://svn.gnome.org/viewvc/beagle?rev=4773&view=rev](http://svn.gnome.org/viewvc/beagle?rev=4773&view=rev)

---

### Post by Conky2000 on 2010-07-06
Hi,

I just ran into this problem and worked around it like this:

go to /usr/bin and mv ssindex to ssindex_org

create a file ssindex and put this into it:
```
#!/usr/bin/perl

$ssindex = `/usr/bin/ssindex_org @ARGV`;

print "DEBUG 1\n";
print "DEBUG 2\n";
print $ssindex;

```

chmod +x the file

you can verify that it's working by doing beagle-extract-content on an xls file.

---

