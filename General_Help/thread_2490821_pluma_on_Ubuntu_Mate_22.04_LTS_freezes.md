---
title: "pluma on Ubuntu Mate 22.04 LTS freezes"
date: 2023-09-17
forum: General Help
---

### Post by electrosteam on 2023-09-17
The Ubuntu Mate install is on a very old laptop that seems reliable in every other way.

When I try to delete a specific character on a pluma generated text file, the machine freezes, then opens up at the signon screen.

I have re-installed pluma to no effect.

Suggestions welcomed.

Keep well,
John.

---

### Post by guiverc on 2023-09-17
Three thoughts come to mind

- I'd explore the file using `hexdump` and check there is nothing unusual in the file.

- I'd  look for clues in system logs (journalctl, dmesg) for clues; given what  you describe - I'd expect a crash file in /var/crash that may also  provide a clue (*the start of the file is pretty easy to read, before it gets to memory dump*)

- I would check the hardware of the device.... (RAM test, SMART or disk health, scan motherboard & look for swollen caps etc)...   though you've described something very specific, which rules out hardware (*unless SMART shows a problem where that file is stored on disk, but it'd show up with other apps which I'm guessing you've ruled out*).   Do note:  *this is something I do automatically if something unusual occurs where I can't find a user/software cause for it; crashes can be diagnostic warnings of coming hardware failures etc.*


---

If the file looks okay, and is read normally in other programs (gedit, featherpad, mousepad or whatever you have available), I'd likely boot a *live* system (Ubuntu-MATE) of *mantic* or the current *development* release and try editing it there...  If it crashes there too, but doesn't in other apps, it is a bug, and I'd file a bug report.  For details on Ubuntu bug filing refer to [https://help.ubuntu.com/community/ReportingBugs](https://help.ubuntu.com/community/ReportingBugs) but Ubuntu-MATE would prefer the bug reported upstream on their GitHub, but using [their discourse]("https://ubuntu-mate.community/") maybe enough, OR if its filed on launchpad & how to re-create it is easily verified, you'll likely find reporting on launchpad is enough.

The *freeze* is probably because of a *loop* I wonder, where more and more memory is being requested, and the final crash & logout is when memory is exhausted.. but I'm guessing here.  System logs I'd hope would provide some clues/proof of this.

---

### Post by electrosteam on 2023-09-17
Thanks for the prod.
Hexdump is a great suggestion.

I did generate a new text file, and adding/deleting various characters did not create a problem.
I will explore the subject system tomorrow with your suggestions.

John.

---

### Post by electrosteam on 2023-09-17
Progress.

hexdump:
 - ascii characters are correct.

copy subject file within its folder:
 - machine crashes when try to open the copy.

nano:
 - successfully deleted offending character,
 - saved.

pluma on (nano edited) file:
 - crashes when try to delete the space left by the character.

LibreOffice Writer:
 - machine crashes when try to launch.

Firefox browsing seems Ok.
LibreCad for small drawings seems OK.
Various read/write to USBs and file system seems Ok.

I suspect I have faulty zones on the hard drive.

This is an old laptop used intensively with Windows for more than 10 years.

What tool is recommended to test the drive and lock out faulty tracks.
Can I install and operate on, say, the top half of the drive ?

John.

---

### Post by MAFoElffen on 2023-09-17
There is this:
```

report=</path/to/original_filename>
report_original=$(mktemp /tmp/report_uncleaned-XXXXX)
mv "$report" "$report_original"
tr -cd '\11\12\40-\176' < "$report_original" > "$report"
rm "$report_original"

```
It's from ReportCleaner(), one of the filters we came up with to clean the UbuntuForum 'system-info' script's report of any non-ascii characters before it tries to upload the report to paste.ubuntu.com... Which doesn't accept any uploads with anything except ascii characters... It uses 'tr', which translates or deletes characters.

Is th drive SMART compatible? If so, then use smartmontools. Good read for you: [https://contabo.com/blog/check-disks-health-linux-smartmontools/](https://contabo.com/blog/check-disks-health-linux-smartmontools/)

---

