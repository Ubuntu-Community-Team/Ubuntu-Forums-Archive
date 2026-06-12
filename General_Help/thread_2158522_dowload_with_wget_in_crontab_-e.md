---
title: "dowload with wget in crontab -e"
date: 2013-06-29
forum: General Help
---

### Post by jefri new line on 2013-06-29
Hy everyone i want to ask something, i used cron to download linux image and make it as schedule. 

so i was had plan to make a schedule to downloading on 21:30 and in days 25,26,27 and month on june

Like this : 

30 21 25,26,27 6 * wget -c [http://kambing.ui.ac.id/iso/fedora/18/Fedora/x86_64/iso/Fedora-18-x86_64-DVD.iso](http://kambing.ui.ac.id/iso/fedora/18/Fedora/x86_64/iso/Fedora-18-x86_64-DVD.iso) /home/jefri

but it doesn't work by far, since in beginning i've tried..!!

Would anyone to help me..!!

---

### Post by Lars Noodén on 2013-06-29
Do they have an rsync version available?  That would allow downloading in full only once and the downloading only the changes, if there are any, on subsequent tries.

The crontab entry looks ok as far as I can tell.  Maybe you should try wrapping wget in a script and calling the script.  Sometimes that helps.

---

### Post by Cheesemill on 2013-06-29
The syntax for your wget command is wrong, it doesn't accept the download location in the format you have written it.

If you put this in your crontab it should download the iso to your home folder...
```
wget -c http://kambing.ui.ac.id/iso/fedora/1...x86_64-DVD.iso
```

---

### Post by SeijiSensei on 2013-06-29
Whose crontab is this in?  jefri's?  (That is, /var/spool/cron/jefri usually created with crontab -e.)

Usually it's preferred to use full paths in crontabs, e.g., /usr/bin/wget rather than just wget, but I doubt that is the problem here.

However you might be encountering this problem as described in the manual page for wget:

Beginning with Wget 1.7, if you use -c on a non-empty file, and it turns out that the
server does not support continued downloading, Wget will refuse to start the download from
scratch, which would effectively ruin existing contents.  If you really want the download
to start from scratch, remove the file.

See if it works without the "-c" parameter.

---

### Post by jefri new line on 2013-06-30
thanks alot for [**[COLOR=#DD4814][B]Lars Noodén **[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=168643")&  [**[COLOR=#000000]SeijiSensei[/COLOR]**]("http://ubuntuforums.org/member.php?u=698195")      :

My ideas was just trying wget to downloading an iso file but in a schedule, or i can say it will downloading automatically..!!

but last night i think the wget script was on working..!

i used this 30 21 25,26,27 6 * wget -c [http://kambing.ui.ac.id/iso/fedora/1...x86_64-DVD.iso]("http://kambing.ui.ac.id/iso/fedora/18/Fedora/x86_64/iso/Fedora-18-x86_64-DVD.iso") and it was done to download 

but the file just put in of the root directory, but if i only used wget and not using crontab at once like this wget -c [http://kambing.ui.ac.id/iso/fedora/1...x86_64-DVD.iso]("http://kambing.ui.ac.id/iso/fedora/18/Fedora/x86_64/iso/Fedora-18-x86_64-DVD.iso") /home/jefri.. The iso file has been  in /home/jefri directory..!! but by using crontab it was nothing in there..!

all i wanted is just about i want to do downloading files no matter what it is, by using crontab -e..

and if downloading is done, files should be in /home/jefri directory..!!


but thanks alot guys..!

:)

---

### Post by coffeecat on 2013-06-30
Support thread.

*Thread moved to **General Help**.*

---

### Post by SeijiSensei on 2013-06-30
Use this command instead:

```
cd /home/jefri; wget ...
```

This will run the wget command from the /home/jefri directory.

---

### Post by achelis on 2013-06-30
If you do
```

man wget

```

You can then see the syntax for wget. One option when downloading just one file could be
```

wget -O <output-file> <URL>

```

What you did was telling wget to first download your iso file and then download from the url /home/jefri which should give the error "scheme missing".
That is with wget you do 
```

wget <URL1> <URL2> .. <URLN>

```
To download multiple urls.

Hope this makes sense :)

---

### Post by jefri new line on 2013-07-01
guys it's not working to use this..!!



cd /home/jefri; wget -c [URL="http://kambing.ui.ac.id/iso/fedora/18/Fedora/x86_64/iso/Fedora-18-x86_64-DVD.iso"]http://kambing.ui.ac.id/iso/fedora/1...x86_64-DVD.iso

[/URL]

---

### Post by jefri new line on 2013-07-01
ALSO IT'S NOT WORKING AS USED THIS..!!



34 10 2,3 7 * cd /jefri  wget -c [http://kambing.ui.ac.id/iso/backtrack/BT5R3-GNOME-32.iso](http://kambing.ui.ac.id/iso/backtrack/BT5R3-GNOME-32.iso)

---

### Post by SeijiSensei on 2013-07-02
The second one won't work because it is missing a semicolon between the commands.  Plus there won't be a /jefri folder unless you created it as root.

Now can you please say more specifically what you mean when you say it isn't working?

Why are you continuing to use the "-c" switch when I specifically pointed out earlier that it may be the source of the problem?

---

### Post by CaptainMark on 2013-07-03
using cd in any script or automated command is generally not great practice, but using wget flags you can specify output directory

---

### Post by jefri new line on 2013-07-04
Seiji  could you some what is it the right command to described what you've pointed..! :)

I've tried the commands above and then i looking to the /jefri with this cd /jefri. And then i was typing ls, but that was nothing any iso file in there. But i go with  wget -c [http://kambing.ui.ac.id/iso/backtrac...3-GNOME-32.iso](http://kambing.ui.ac.id/iso/backtrac...3-GNOME-32.iso) /jefri, downloading was running and the backtrack iso was in there at /jefri ..!!

options -c in wget it's to make downloading possible to continues later on if our internet connection is disconnection..

so that's why i kept use -c in wget..!!

---

### Post by jefri new line on 2013-07-04
for captainmark, could you show me the ideas about to use wget flags related to my case..!

i want iso file be in /jefri folder, not in /root folder..!!

captainmark, give me an example please..!

:)

---

### Post by jefri new line on 2013-07-04
i had tried using cd in crontab -e such like this:


30 21 25,26,27 6 * cd /home/jefri; wget -c [http://kambing.ui.ac.id/iso/fedora/1...x86_64-DVD.iso]("http://kambing.ui.ac.id/iso/fedora/18/Fedora/x86_64/iso/Fedora-18-x86_64-DVD.iso")

30 21 25,26,27 6 * wget -O  /home/jefri  -c [http://kambing.ui.ac.id/iso/fedora/1...x86_64-DVD.iso]("http://kambing.ui.ac.id/iso/fedora/18/Fedora/x86_64/iso/Fedora-18-x86_64-DVD.iso")


captainmark, that was all i had tried and not bring me what i really wanted

---

### Post by CaptainMark on 2013-07-04
yes of course ```
wget -P /jefri/ http://upload.wikimedia.org/wikipedia/commons/6/63/Wikipedia-logo.png
```This downloads the wikipedia logo straight into /jefri without modifying its file name, I believe the P is for parent as in parent directory to use

---

### Post by Lars Noodén on 2013-07-04
It can be **-P** or **--directory-prefix=**.  

[wget](http://manpages.ubuntu.com/manpages/raring/en/man1/wget.1.html) has a surprising number of other options described in the manual page.  Also *wget --help* gives a short summary.

---

### Post by jefri new line on 2013-07-05
its works thanks alot to captainmark..!!


:)

---

