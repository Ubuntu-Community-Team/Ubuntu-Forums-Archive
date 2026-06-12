---
title: "So is GIMP STILL 8-bit color?"
date: 2012-12-16
forum: General Help
---

### Post by Bartender on 2012-12-16
I thought that the latest version of GIMP (2.8.2 is what I have now, following [these instructions]("www.webupd8.org/2012/05/gimp-28-stable-finally-available-for.html") from WEBUPD8) and there's still no "Precision" choice under Image.

So this website indicates that 16-bit is ready if you're willing to do some [compiling]("http://www.gimpusers.com/news/00422-16-bit-goat-invasion-ready").  I followed the link to the [instructions]("http://www.gimpusers.com/tutorials/compiling-gimp-for-ubuntu").  I've been hanging around Linux for a while now, but not ready to try all that on our daily-use PC.

Besides, those instructions are months old, and for 2.8-RC1.  I woulda thought 2.8.2 would be further along.  Maybe they pulled 16-bit back out?

Does anybody have the latest news on this?  

Maybe it's time to just give up and buy Photoshop for the Windows side of our dual-boot?

---

### Post by Feared on 2012-12-16
GIMP still doesn't have 16bit support out of the box with Ubuntu 12.10. The article you linked said 16 and 32 bit support were expected in the 2.10 release of GIMP. Considering we're still on 2.8 it might be a while before we see this update on 12.04 or 12.10 Ubuntu without compiling it ourselves or using a user PPA. There might be a nightly gimp available via PPA, you may want to look into that if you're interested.

Also, another thing to note. Photoshop CS2 (and CS3?) seem to work flawlessly in WINE if you can't seem to get GIMP doing what you want it to.

---

### Post by mc4man on 2012-12-16
Atm if nothing easier available then you could basically follow those instructions.
Use git clone for all 3, - babl, gegl, gimp
Change **all instances** of "gimp-2.8" to gimp-2.9 in the instru's
Should work ok. You don't need to remove current gimp, they can co-exist

An alt. to some of the instru's
You could just build locally in your Home folder some where instead of temp & keep the builds/sources for updating or make uninstall
With proper naming you could likely use checkinstall instead of make install

---

### Post by cscj01 on 2013-01-09
> **mc4man said:**
> Atm if nothing easier available then you could basically follow those instructions.
Use git clone for all 3, - babl, gegl, gimp
Change **all instances** of "gimp-2.8" to gimp-2.9 in the instru's
Should work ok. You don't need to remove current gimp, they can co-exist

An alt. to some of the instru's
You could just build locally in your Home folder some where instead of temp & keep the builds/sources for updating or make uninstall
With proper naming you could likely use checkinstall instead of make install

I have followed the same set of instructions as Bartender indicated plus your hints.  My install is in a folder in my home directory.  After using git to acquire gimp, babl, and gegl, I got through the babl compile.  However, with the gegl compile (actually on the autoconfig step), I am told I need GLIB 2.28.0 or better.  I am on Precise and my system is up to date.  Will installing GLIB 2.28.0 break something?  The only PPAs I use are for darktable, hugin, and Canonical Partners.

Thanks for your help.  I'm new at compiling from source.

---

### Post by AstroLlama on 2013-01-09
gimp 2.10 is close be patient!

if you need to buy photoshop to get your work done, then that's what you should do, it would be an investment. plus they have other versions that aren't the "full package" which are much cheaper than the professional version with all the bells and whistles.

But don't think that just because you have deeper color depth all of a sudden your photoshop skills will rise exponentially. believe me I'm a musician and I can tell you that using good equipment doesn't automagically make you good! (but it will make you better if you're already good) :)

---

### Post by Futant on 2013-01-09
> **AstroLlama said:**
> gimp 2.10 is close be patient!

But don't think that just because you have deeper color depth all of a sudden your photoshop skills will rise exponentially. believe me I'm a musician and I can tell you that using good equipment doesn't automagically make you good! (but it will make you better if you're already good) :)
  
Agreed...

---

### Post by cscj01 on 2013-01-10
To AstroLlama and Futant:
I appreciate your views, but that is not the question I asked.  Perhaps I need to reenter this as a separate question.  It's not just about higher bit depth, but better samples for downsizing as just one example.  I could go on, but that would serve no purpose.

Could anyone address my question as to whether installing GLIB 2.28.0 will cause problems in my environment?

---

### Post by mc4man on 2013-01-10
> **cscj01 said:**
> To AstroLlama and Futant:
I appreciate your views, but that is not the question I asked.  Perhaps I need to reenter this as a separate question.  It's not just about higher bit depth, but better samples for downsizing as just one example.  I could go on, but that would serve no purpose.

Could anyone address my question as to whether installing GLIB 2.28.0 will cause problems in my environment?
I don't have 12.04 installed atm  so don't know if a gimp 2.9+ build is viable but can say your glib version is already higher (better) than 2.28 (2.32

make sure this is installed
```
sudo apt-get install libglib2.0-dev
```

---

### Post by cscj01 on 2013-01-11
> **mc4man said:**
> I don't have 12.04 installed atm  so don't know if a gimp 2.9+ build is viable but can say your glib version is already higher (better) than 2.28 (2.32

make sure this is installed
```
sudo apt-get install libglib2.0-dev
```

Thanks.  That was what I needed.

---

### Post by cscj01 on 2013-01-11
> **mc4man said:**
> Atm if nothing easier available then you could basically follow those instructions.
Use git clone for all 3, - babl, gegl, gimp
Change **all instances** of "gimp-2.8" to gimp-2.9 in the instru's
Should work ok. You don't need to remove current gimp, they can co-exist

An alt. to some of the instru's
You could just build locally in your Home folder some where instead of temp & keep the builds/sources for updating or make uninstall
With proper naming you could likely use checkinstall instead of make install

I have Gimp 2.9 installed and working thanks to you.  I do have a couple of questions.  You mention a couple of alternate takes on the instructions.  The first has to do with building in my home directory (which I did) and keeping the builds for updating and make uninstall.  I'm not quite sure what this means.  I know make uninstall will remove the install, but how do I go about updating?  Does that involve doing a new git and going through the steps again?  If so, do I remove the original gits?

The second has to do with appropriate naming to use checkinstall instead of make install.  What is involved here?

Thanks for your help.

---

### Post by mc4man on 2013-01-11
> **cscj01 said:**
> I have Gimp 2.9 installed and working thanks to you.  I do have a couple of questions.  You mention a couple of alternate takes on the instructions.  The first has to do with building in my home directory (which I did) and keeping the builds for updating and make uninstall.  I'm not quite sure what this means.  I know make uninstall will remove the install, but how do I go about updating?  Does that involve doing a new git and going through the steps again?  If so, do I remove the original gits?

The second has to do with appropriate naming to use checkinstall instead of make install.  What is involved here?

Thanks for your help.

Atm I'm only on 13.04 & don't have 2.9+ installed, maybe I do later today to 'refresh' my memory & give you exact, correct advice on all.
So check back later...
(as far as updating git sources generally I cd to source, run a 
make distclean
git pull
Then build as before for all 3, new files will overwrite the old so no need usually to remove 1st.

(when I did have it in place made a new .desktop to add to plank launcher (or unity launcher), can also post example if desired

One of the good reasons to install using checkinstall is that you'll have packages - so if an updated build(s) proved unsuitable it's quite simple to re-install using the previous packages

---

### Post by mc4man on 2013-01-12
Put up a 12.04 install so some example checkinstall commands - 
blue is an optional option, you'd need to adjust path to suit (red) or just leave out. If leaving out I'd move the .debs out of source folders into build folder (if that's how you did
In my case created a gimp_build folder in home folder to do all the builds - screen


```
sudo checkinstall --pkgname=babl --pkgversion=0.1.10 --backup=no --deldoc=yes \
--fstrans=no --deldesc=yes --delspec=yes --default [COLOR="Blue"]--pakdir=[/COLOR][COLOR="Red"]"$HOME/gimp_build"[/COLOR]
```

```
sudo checkinstall --pkgname=gegl --pkgversion=0.2.1 --backup=no --deldoc=yes \
--fstrans=no --deldesc=yes --delspec=yes --default [COLOR="Blue"]--pakdir=[/COLOR][COLOR="Red"]"$HOME/gimp_build"[/COLOR]

```
```
sudo checkinstall --pkgname=gimp-2.9 --pkgversion="2.9-git-$(date +%Y%m%d)" \
--backup=no --deldoc=yes --fstrans=no --deldesc=yes --delspec=yes \
--default [COLOR="Blue"]--pakdir=[/COLOR][COLOR="Red"]"$HOME/gimp_build"[/COLOR]
```

If you want some add. control on options leave out the --default & follow prompts

(I'd somewhat pay attention to the configure results of gegl & definitely pay to those of gimp, add support if missing & needed (search synaptic based on missing support name - look for a dev package, then rerun either the "./autogen.sh --prefix=/opt/gimp-2.9" or after an initial autogen you can just use 
./configure --prefix=/opt/gimp-2.9
or
./configure --prefix=/opt/gimp-2.9 some add. configure options - ./configure --help will show

---

