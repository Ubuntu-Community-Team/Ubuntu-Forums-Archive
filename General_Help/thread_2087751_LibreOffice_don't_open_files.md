---
title: "LibreOffice don't open files"
date: 2012-11-24
forum: General Help
---

### Post by mr.suchy on 2012-11-24
Hi everyone,

I have Xubuntu  right now and I install LibreOffice from repository. Right now I can't open any files. When I run program from terminal:

```
libreoffice --calc
```

nothing was happening. I have a fresh version of Xubuntu 12.10. In log I can't any error the same in console. Sorry for my language.

Best regards

---

### Post by Hagar Delest on 2012-11-24
You can first try to [reset your OpenOffice user profile (click this hyperlink)](http://forum.openoffice.org/en/forum/viewtopic.php?p=58403#p58403).

If no change, were you able to open them before? With what application or Xubuntu flavor?

You can try to install LO or Apache OpenOffice with the debs packages (more robust method IMHO): [[Ubuntu] Installing OOo on Debian and Co.](http://forum.openoffice.org/en/forum/viewtopic.php?f=16&t=68)

---

### Post by vasa1 on 2012-11-24
> **mr.suchy said:**
> Hi everyone,

I have Xubuntu  right now and I install LibreOffice from repository. Right now I can't open any files. When I run program from terminal:

```
libreoffice --calc
```

nothing was happening. I have a fresh version of Xubuntu 12.10. In log I can't any error the same in console. Sorry for my language.

Best regards

Have you tried```
libreoffice3.6 --calc
```?

---

### Post by Hagar Delest on 2012-11-24
On Ubuntu 12.10:
libreoffice --calc works fine.
libreoffice3.6 --calc does not.

---

### Post by vasa1 on 2012-11-24
You can look at the .desktop file in /usr/share/applications called LibreOffice3.x Calc. Open it with a text editor such as Mousepad or gedit. Then look for a line like this:
Exec=libreoffice3.6 --calc %U

I have LibreOffice 3.6 and so my .desktop file is "LibreOffice3.6 Calc". You may want to leave out the %U or whatever follows --calc when starting from the terminal.

---

### Post by vasa1 on 2012-11-24
> **Hagar Delest said:**
> On Ubuntu 12.10:
libreoffice --calc works fine.
libreoffice3.6 --calc does not.
I think the former is for Unity. The latter works with Lubuntu although the .desktop file looks like this:
```
[Desktop Entry]
Version=1.0
Terminal=false
Icon=libreoffice3.6-calc
Type=Application
Categories=Office;Spreadsheet;X-Red-Hat-Base;X-MandrivaLinux-Office-Spreadsheets;
Exec=libreoffice3.6 --calc %U
MimeType=application/vnd.oasis.opendocument.spreadsheet;application/vnd.oasis.opendocument.spreadsheet-template;application/vnd.sun.xml.calc;application/vnd.sun.xml.calc.template;application/msexcel;application/vnd.ms-excel;application/vnd.openxmlformats-officedocument.spreadsheetml.sheet;application/vnd.ms-excel.sheet.macroenabled.12;application/vnd.openxmlformats-officedocument.spreadsheetml.template;application/vnd.ms-excel.template.macroenabled.12;application/vnd.ms-excel.sheet.binary.macroenabled.12;text/csv;application/x-dbf;text/spreadsheet;application/csv;application/excel;application/tab-separated-values;application/vnd.lotus-1-2-3;application/vnd.oasis.opendocument.chart;application/vnd.oasis.opendocument.chart-template;application/x-dbase;application/x-dos_ms_excel;application/x-excel;application/x-msexcel;application/x-ms-excel;application/x-quattropro;application/x-123;text/comma-separated-values;text/tab-separated-values;text/x-comma-separated-values;text/x-csv;
Name=LibreOffice 3.6 Calc
GenericName=Spreadsheet
GenericName[zu]=Ikhasi lokubala
Comment=Perform calculations, analyze information and manage lists in spreadsheets by using Calc.
Comment[zu]=Perform calculations, analyze information and manage lists in spreadsheets by using Calc.
InitialPreference=5
X-Ayatana-Desktop-Shortcuts=X-New
[X-New Shortcut Group]
Name=New Spreadsheet
Name[zu]=New Spreadsheet
Exec=libreoffice --calc %U
TargetEnvironment=Unity

```

Note the last line versus the seventh line.

---

### Post by Hagar Delest on 2012-11-24
Strange to see twice the exec line!

---

### Post by vasa1 on 2012-11-24
> **Hagar Delest said:**
> Strange to see twice the exec line!
Yes!
On Lubuntu, libreoffice3.6 --calc works whereas libreoffice --calc doesn't. Let's see what OP comes up with.
BTW, my LibreOffice is direct from libreoffice.org and not from a ppa because I remember you making the point about how distro mods may have unintended consequences.

---

### Post by mr.suchy on 2012-11-25
Okay I check this problem once again and right know I solved a few problem but still can't open a file in CALC. I had this problem

```
mrsuchy@xubuntu-desktop:~/Dropbox/Wspólne$ libreoffice --calc Finanse.ods
Fontconfig warning: "/usr/lib/libreoffice/share/fonts/truetype/fc_local.conf", line 12: Having multiple <family> in <alias> isn't supported and may not works as expected

```I remove duplicate entry and now my fc_local.conf look like that:
```
<?xml version="1.0"?>
<!DOCTYPE fontconfig SYSTEM "/etc/fonts/conf.d/fonts.dtd">
<fontconfig>

    <!-- Alias similar/metric-compatible families from various sources: -->

    <alias binding="same">
      <family>Arial Narrow</family>
      <default>
      <family>Arial Narrow</family>
      </default>
    </alias>

<!-- -->
    <alias binding="same">
      <family>Arial Narrow</family>
      <accept>
      <family>Liberation Sans Narrow</family>
      </accept>
    </alias>
<!-- -->

</fontconfig>

```When I enter this command in terminal LibreOffice display splash screen but nothing is happening

```
mrsuchy@xubuntu-desktop:~/Dropbox/Wspólne$ libreoffice --calc Finanse.ods
mrsuchy@xubuntu-desktop:~/Dropbox/Wspólne$ 

```

---

### Post by mr.suchy on 2012-11-26
up

---

### Post by Hagar Delest on 2012-11-26
What about installing Apache OpenOffice?

---

### Post by mr.suchy on 2012-11-27
@Hagar Delest what it's Apache OpenOffice ? This is old OpenOffice ?

---

### Post by Hagar Delest on 2012-11-27
OpenOffice.org has been donated by Sun to the Apache Foundation (last year). After some months of "hidden" work to clear intellectual property issues with code that doesn't fit the Apache License (hence those who said that OOo was dead), the development has just continued.

So yes, Apache OpenOffice is now the successor of OpenOffice.org. The code is almost the same and will now continue to evolve to improve the application. The main point is that the team is focused on a high quality product: the target is not to release often but to release something stable.

Personally, I can't use LO because of some of their "features" that are show stopper for me and because it seems to be more buggy. Moreover, I think the Apache model will prevail and I'm more in line with their philosophy.

You can install both suites if you use the .debs from their websites and then have your own idea.

---

### Post by mr.suchy on 2012-11-28
Thanks for advice. Yesterday I did few tests and I have this:

1. LibreOffice Calc or Writer works fine if I create a new document. Whatever it's a .ods or .xls.
2.  I have problem to open one file with .ods enlargement. But the same file open in Ubuntu 12.04 works fine and Windows with LibreOffice.

3. When I unrar this file and delete content.xml Xubuntu can open this file. 

I don't understand why LibreOffice has problem with open the defulat enlargement (I mean .ods) ?:(  Right now I must create new file .ods and repeat everything from old file to new one. 

Thanks for help in this thread, send PW and all. My english is poor so sorry for any mistakes.

Best regards!:)

---

### Post by Vaphell on 2012-11-28
enlargement? you mean extension?

---

### Post by mr.suchy on 2012-11-28
Yes, sorry for mistake.

---

### Post by Hagar Delest on 2012-11-28
Then try to open it and save it under another name, it may help (I mean the resaving, not the renaming).

---

### Post by vasa1 on 2012-11-28
> **Hagar Delest said:**
> OpenOffice.org has been donated by Sun to the Apache Foundation (last year). ....
Sun? Looked more like a donation by LE to RW ;)

Anyway, this thread is about LibreOffice. I'm not saying I don't mind reading about why AOO is, or maybe, superior. Perhaps a thread of its own would be best.

---

### Post by Hagar Delest on 2012-11-29
Oops, you're right! It has been given by Oracle (Larry Ellison) since they had bought Sun few months before.

---

### Post by mr.suchy on 2012-12-01
I want to install libreoffice once again but I have problem with package. When I install libreoffice something is wrong and I must re pare pakage with:

```
apt-get -f install
```

But I get error:
```
Zostan&#261; zainstalowane nast&#281;puj&#261;ce dodatkowe pakiety:
  libreoffice-common
Sugerowane pakiety:
  libreoffice-style-hicontrast libreoffice-style-crystal
  libreoffice-style-oxygen
Zostan&#261; zainstalowane nast&#281;puj&#261;ce NOWE pakiety:
  libreoffice-common
0 aktualizowanych, 1 nowo instalowanych, 0 usuwanych i 2 nieaktualizowanych.
15 nie w pe&#322;ni zainstalowanych lub usuni&#281;tych.
Konieczne pobranie 0 B/16,3 MB archiwów.
Po tej operacji zostanie dodatkowo u&#380;yte 70,2 MB miejsca na dysku.
Kontynuowa&#263; [T/n]? t
(Odczytywanie bazy danych ... 174515 plików i katalogów obecnie zainstalowanych.)
Rozpakowywanie pakietu libreoffice-common (z .../libreoffice-common_1%3a3.6.2~rc2-0ubuntu4_all.deb) ...
dpkg: error processing /var/cache/apt/archives/libreoffice-common_1%3a3.6.2~rc2-0ubuntu4_all.deb (--unpack):
 próba nadpisania "/usr/bin/soffice", który istnieje tak&#380;e w pakiecie openoffice.org-debian-menus 3.3-9556
Brak raportu programu apport, poniewa&#380; osi&#261;gni&#281;to limit MaxReports
                                                                  rmdir: nie uda&#322;o si&#281; usun&#261;&#263; `/var/lib/libreoffice/share/prereg/': Nie ma takiego pliku ani katalogu
rmdir: nie uda&#322;o si&#281; usun&#261;&#263; `/var/lib/libreoffice/share/': Katalog nie jest pusty
rmdir: nie uda&#322;o si&#281; usun&#261;&#263; `/var/lib/libreoffice/program/': Nie ma takiego pliku ani katalogu
rmdir: nie uda&#322;o si&#281; usun&#261;&#263; `/var/lib/libreoffice': Katalog nie jest pusty
rmdir: nie uda&#322;o si&#281; usun&#261;&#263; `/var/lib/libreoffice': Katalog nie jest pusty
Przetwarzanie wyzwalaczy pakietu desktop-file-utils...
Przetwarzanie wyzwalaczy pakietu shared-mime-info...
Przetwarzanie wyzwalaczy pakietu gnome-icon-theme...
Przetwarzanie wyzwalaczy pakietu hicolor-icon-theme...
Przetwarzanie wyzwalaczy pakietu man-db...
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 /var/cache/apt/archives/libreoffice-common_1%3a3.6.2~rc2-0ubuntu4_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

What is wrong ? A few minutes ago I install Apache OpenOffice and my file open but I want try once again with libreoffice.

---

### Post by Hagar Delest on 2012-12-01
Difficult to say without understanding the language...

But basically, install Synaptic and remove any package related to LibreOffice or openOffice.org first.

---

### Post by xadder on 2013-08-15
I am having similar problems with a new installation of Xubuntu 13.04   (libreoffice 4.0.2.2). If I try libreoffice or libreoffice --calc  I just get a menu asking for the type of file, with no sign of a spreadsheet option. I tried with .xls and .ods files.   If I run just libreoffice --calc, I get an empty text document.

I looked at the links given above about profiles, but they seem old, and I don't see the mentioned files in my filesystem.

Help, please!

---

### Post by xadder on 2013-08-15
Just solved my own problem. when I used synaptic, I could see that the meta-package libreoffice-calc wasn't installed. The "libreoffice" I got from the Xubuntu install seems to be just the libreoffice-writer. Odd.

---

