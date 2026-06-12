---
title: "I wana convert a UIF To a ISO File"
date: 2007-06-24
forum: General Help
---

### Post by FAS786 on 2007-06-24
I wana convert a UIF To a ISO File
Are there any converters which work with Ubuntu

Magic ISO is not ubuntu type

i hear you can try something with wine any instructions im a newbe?

---

### Post by greeneggsnsam on 2007-06-24
Yes, MagicISO can be installed and is usable with Wine- just get the MagicISO exe file and run it with Wine, then you can change the file types or whatever you want to do using MagaicISO under Wine.

---

### Post by uk_mangat on 2008-03-22
how to executed file for .uif

---

### Post by wesleybailey on 2008-03-29
You can use UIF2ISO in Ubuntu, and use it to convert the .uif file to an .iso. Then you can burn it with k3b.

1. You need to install zlib and OpenSSL with apt-get.
```

sudo apt-get install zlib1g zlib1g-dev libssl-dev

```
2. You can download UIF2ISO with wget from a terminal, or from the author&#8217;s site here.
```

wget http://aluigi.altervista.org/mytoolz/uif2iso.zip

```

3. Unzip, make, and make install the file, and finally.
```

uif2iso example.uif output.iso

```

If you need more help or step-by-step instructions following this [tutorial]("http://wesleybailey.com/blog/2008/03/28/linux-uif-to-iso/").

---

### Post by ibuclaw on 2008-03-29
[NeroLinux is a great tool for this too.]("http://www.nero.com/eng/downloads-linux3-trial.php")

Something that newly converts can consider to use to make the transient change easier.

Regards

---

### Post by 1/0 on 2008-04-12
> **tinivole said:**
> [NeroLinux is a great tool for this too.]("http://www.nero.com/eng/downloads-linux3-trial.php")

Something that newly converts can consider to use to make the transient change easier.

Regards

I took a look at nero (though I personally dislike proprietary programs) but I can't seem to find any support for uif images. Does nero really support uif?

---

### Post by wesleybailey on 2008-04-12
I did some researching, and it looks like Nero does not support UIF Images.
According to the [manual]("http://ftp6.nero.com/user_guides/nero8/burningrom/NeroBurningRom_Enu.pdf") Nero 8(latest version) only these formats are supported: 

CD/DVD-ROM (ISO)
CD/DVD/HD DVD-ROM/Blu-ray Disc(UDF)
CD/DVD-ROM(UDF/ISO)

---

### Post by derbouka on 2008-04-22
uif2iso worked fine! 
Why isn't it in the repositorie?

---

### Post by DBrocks on 2008-04-22
Would you please mark this thread as solved. It helps out people trying to find an answer to their questions, and it helps us as the people who try to solve other's problems. 

Thanks!

---

### Post by Copter on 2008-06-11
> **wesleybailey said:**
> You can use UIF2ISO in Ubuntu, and use it to convert the .uif file to an .iso. Then you can burn it with k3b.


Thanks a lot! Works like a charm.

copter :]

---

### Post by BLTicklemonster on 2008-06-18
> **wesleybailey said:**
> You can use UIF2ISO in Ubuntu, and use it to convert the .uif file to an .iso. Then you can burn it with k3b.

1. You need to install zlib and OpenSSL with apt-get.
```

sudo apt-get install zlib1g zlib1g-dev libssl-dev

```
2. You can download UIF2ISO with wget from a terminal, or from the author’s site here.
```

wget http://aluigi.altervista.org/mytoolz/uif2iso.zip

```

3. Unzip, make, and make install the file, and finally.
```

uif2iso example.uif output.iso

```

If you need more help or step-by-step instructions following this [tutorial]("http://wesleybailey.com/blog/2008/03/28/linux-uif-to-iso/").

Looks like it's working!!! thanks!

---

