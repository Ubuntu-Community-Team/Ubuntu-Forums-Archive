---
title: "Installing digikam5 onto Lubuntu 17.10"
date: 2018-01-11
forum: General Help
---

### Post by hundred1906 on 2018-01-11
I have Digikam5 installed onto a 32bit virtual machine under Lubuntu 16.04.

After switching my host onto a 64 bit machine I now want to install Digikam5 onto a 64 bit Lubuntu at 17.10. When I try this I am advised of many unmet dependencies.
> The following packages have unmet dependencies:
 digikam5 : Depends: libjasper1 which is a virtual package and is not provided by any available package

            Depends: libmarblewidget-qt5-23 (>= 4:15.12.0) which is a virtual package and is not provided by any available package

            Depends: libopencv-contrib2.4v5 which is a virtual package and is not provided by any available package

            Depends: libopencv-core2.4v5 which is a virtual package and is not provided by any available package

            Depends: libopencv-imgproc2.4v5 which is a virtual package and is not provided by any available package

            Depends: libopencv-objdetect2.4v5 which is a virtual package and is not provided by any available package

            Depends: libpng12-0 (>= 1.2.13-4) which is a virtual package and is not provided by any available package

 libqtav : Depends: libass5 (>= 0.13.0) which is a virtual package and is not provided by any available package

           Depends: libavcodec-ffmpeg56 (>= 7:2.4) which is a virtual package and is not provided by any available package
 or
                    libavcodec-ffmpeg-extra56 (>= 7:2.4) which is a virtual package and is not provided by any available package

           Depends: libavdevice-ffmpeg56 (>= 7:2.4) which is a virtual package and is not provided by any available package

           Depends: libavfilter-ffmpeg5 (>= 7:2.4) which is a virtual package and is not provided by any available package

           Depends: libavformat-ffmpeg56 (>= 7:2.4) which is a virtual package and is not provided by any available package

           Depends: libavresample-ffmpeg2 (>= 7:2.4) which is a virtual package and is not provided by any available package

           Depends: libavutil-ffmpeg54 (>= 7:2.4) which is a virtual package and is not provided by any available package

           Depends: libswresample-ffmpeg1 (>= 7:2.4) which is a virtual package and is not provided by any available package

           Depends: libswscale-ffmpeg3 (>= 7:2.4) which is a virtual package and is not provided by any available package


What I did was to add a repository, update then try to install

```
sudo add-apt-repository ppa:philip5/extra
sudo apt-get update
sudo apt-get install kdenlive5
```

Am I being informed that these packages really are not available under release 17.10 - or have I just screwed up elsewhere?

---

### Post by Holger_Gehrke on 2018-01-11
The PPA from which you're trying to install does not offer packages for 17.10 (yet ?). And why should it ? The packages in the normal repositories for Artful Aardvark are very close in version numbers to those offered by this personal package archive for Trusty Tahr to Zesty Zappus. In your place I'd remove the ppa from my sources and try the version in the repositories.

Holger

---

### Post by hundred1906 on 2018-01-12
Holger, thank you for the reply. The version in the repositories is V4, I prefer using V5 now. I knew it was going to be a mistake loading up the 17.10 version of Lubuntu.

So I'll just continue using the 16.04 version for now.

---

### Post by Holger_Gehrke on 2018-01-12
How do you get the idea it's version 4 ? I'm running XUbuntu 17.04 and the version from the repositories identifies as version 5.4.0 on the splash screen and in the help->about menü item. I don't know what the '4:' at the beginning of the version-field in the package list in synaptic means, but it is not part of the version number of the software. And if I read the contents of the repository right, on 17.10 you should be getting version 5.6 of digikam from the repo.

Holger

---

### Post by hundred1906 on 2018-01-12
Actually the repository now only has the one entry and it does not say what version it is. I only assumed it was V4xx.. without loading it up because 

[INDENT]a) when I set the ppa given on the digikam page a second entry appeared specifically for V5... , so I assumed the first was for V4
b) my Lubuntu 16.04 has both entries - and both are loaded in my case
c) digikam say you can load either so I assumed having two entries in the repository was normal[/INDENT]

So now I have loaded it and in fact it is, as Holger says, V5 (V5.6).

Hooray.

---

