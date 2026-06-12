---
title: "missing X11 fonts in Edgy"
date: 2006-12-06
forum: General Help
---

### Post by abovett on 2006-12-06
Hi.

Having some problems in Edgy with a (python) programs which works fine under Dapper. It seems that some fonts are not available - xlsfonts on Dapper shows fonts such as [B]-bitstream-bitstream vera sans mono-bold-o-normal--0-0-0-0-c-0-iso8859-1
[/B] but these are not available on Dapper (even though the **ttf-bitstream-vera** package is installed). The Python/Tk program calls for "Bitstream Vera Sans" and this works under Dapper but not under Edgy - I get a default (serif'd) font.

Any suggestions?

(by the way - I've corrected the error in the xorg.conf file which had "X11/fonts" instead of "fonts/X11")

Thanks

Andy

---

### Post by cmayo on 2006-12-31
I did the following:

apt-get install ttmkfdir

ttmkfdir -o fonts.dir -d /usr/share/fonts/truetype/ttf-bitstream-vera/

added to /etc/X11/xorg.conf:
FontPath        "/usr/share/fonts/truetype/ttf-bitstream-vera"

restarted X

---

### Post by abovett on 2007-01-25
Thanks.

I have since found a simpler fix which seems to work, but your answer gave me the clue. I compared dapper, edgy and feisty and found that there was a fonts.dir file missing in edgy. The solution is to copy fonts.scale to fonts.dir in the relevant directory - in this case /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType, i.e.

```
sudo cd /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
sudo cp fonts.scale fonts.dir
```

It appears to be OK in feisty.

Thanks

Andy

---

### Post by yabbadabbadont on 2007-01-26
/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType doesn't even exist on my Dapper install... :(  I ended up having to run mkfontscale and mkfontdir on each of the directories in /usr/share/fonts/type1 and /usr/share/fonts/truetype.  I also added a FontPath entry for each of them to the Files section of /etc/X11/xorg.conf.  Only then did those fonts show up in xfontsel.

---

### Post by Ruth Lazkoz on 2007-02-05
> **yabbadabbadont said:**
> /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType doesn't even exist on my Dapper install... :(  I ended up having to run mkfontscale and mkfontdir on each of the directories in /usr/share/fonts/type1 and /usr/share/fonts/truetype.  I also added a FontPath entry for each of them to the Files section of /etc/X11/xorg.conf.  Only then did those fonts show up in xfontsel.

Hi,

I am desperate trying for Mathematica to use postcript fonts. I found this thread and thought this was going to be the solution. 

As you talk about the bitstream-vera font I tried to make it visible on xlsfonts.

I have run all the commands you give here, but nothing works. This font does not seem to be there when I type xlsfonts, but it seem to be available from System-Preferences-Typography.

I have read somewhere else that one needs to set the permissions properly. I have done chmod a+r+w+x *.ttf inside the directory but it did not work.

Can you give me hints?

Thanks,

Ruth

---

### Post by yabbadabbadont on 2007-02-05
In the time since I made that post, I have reinstalled.  This time I made sure that x-ttcidfont-conf was installed and the appropriate directory and links are there like they should be.  I'm sure that I checked to see if that package was installed before but, whatever... It all worked without any special effort this time around.  The only suggestion I can make to you is to make sure that x-ttcidfont-conf is installed and, even if it is, to force it to be reinstalled.

---

