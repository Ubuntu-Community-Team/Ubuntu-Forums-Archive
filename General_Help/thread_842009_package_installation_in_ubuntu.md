---
title: "package installation in ubuntu"
date: 2008-06-26
forum: General Help
---

### Post by vinod_jaiswal18 on 2008-06-26
Hello guys,
i am an perfect beginner in Linux.:)
i hav just Shifted from Windows vista last week.:popcorn::KS
Please guide me through package installation ....of.:
[COLOR="Red"]1)RPM Package (.rpm)

2)Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)[/COLOR]

i hav tried them using these guidance, but failed.:
:confused:
[http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

SO...help me..with easy instructions.:guitar:
thanks
regards

---

### Post by iaculallad on 2008-06-26
> **vinod_jaiswal18 said:**
> Hello guys,
i am an perfect beginner in Linux.:)
i hav just Shifted from Windows vista last week.:popcorn::KS
Please guide me through package installation ....of.:
[COLOR="Red"]1)RPM Package (.rpm)[/COLOR]

-You need to install alien application so you can convert RPM files to Ubundu/Debian readable format (.deb):

```
sudo apt-get install alien
```

Then install the converted RPM files to DEB files using the command:

```
sudo dpkg -i Converted_File.deb
```


> **vinod_jaiswal18 said:**
> 
2)Source Package (.tar, .tar.gz, .tgz, .tar.bz, ...)[/CODE]

-Unpack the file and you might need to compile those files inside the archived file:

Basically, with these three commands:

```

./configure
sudo make
make install

```

---

### Post by ramjet_1953 on 2008-06-27
A few of pointers, if I may:

1. using Alien with RPM packages is a LAST RESORT and often the created deb package won't run.

2. If you enable the extra repositories in Synaptic, there is a huge selection of programs available. Also the Get Deb site has some more.

3. Always Google for a deb package. i.e. if you are looking for a package called fred, just Google for fred .deb

4. Compiling from source is not for beginners. You need to learn to crawl, before you walk. It is NOT as simple as some may say. You can easily get caught in 'dependency hell' and it will drive you crazy, unless you know what you are doing. Before even attempting to compile from source, google for some tutorials and work through the lessons, so you know what you are attempting.

Regards,
Roger :cool:

---

