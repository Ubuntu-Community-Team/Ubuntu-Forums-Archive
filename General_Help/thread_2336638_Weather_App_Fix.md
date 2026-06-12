---
title: "Weather App Fix"
date: 2016-09-09
forum: General Help
---

### Post by ubisrbina on 2016-09-09
As of late the weather app on my Ubuntu Mate machine has stopped working. The reason for that is that the site where the app would get it's info got closed down/changed. I found this solution online and wanted to share it with you just in case there is someone else out there with the same issue. [http://askubuntu.com/questions/817083/my-weather-widget-is-not-working](http://askubuntu.com/questions/817083/my-weather-widget-is-not-working)

Enable sources downloading in APT. You can do this in the *System* / *Administration* / *Software and Updates* dialog, by checking the *Source code* item in the *Ubuntu software* tab. You can also enable them in the /etc/apt/sources.list file.

Using the MATE Terminal (or any other terminal program or directly in  the Linux console), create a temporary directory where you can compile  the libmateweather sources (for example, mkdir newlibmateweather) then change to that directory (cd newlibmateweather).

Download the sources of libmateweather (apt-get source libmateweather), note this does not require to use sudo).

Install the dependencies required to build the package (sudo apt-get build-dep libmateweather). Also install the *fakeroot* package (sudo apt-get install fakeroot).

Edit the ./libmateweather-1.12.1/libmateweather/weather-metar.c file, changing the following lines:
At line 525, change "National Weather Service" to "AVIATION WEATHER CENTER"

At line 553, change "http://weather.noaa.gov/mgetmetar.php" to "http://aviationweather.gov/metar/data"
At line 554, change "cccc" to "ids"

Change to the library source directory (cd libmateweather-1.12.1/).

Create .deb packages (dpkg-buildpackage -rfakeroot -uc -b). This may take a while. At the end you will find several .deb files **in the parent directory**  according to the architecture of your computer (for example, in mine,  that created libmateweather1_1.12.1-1_amd64.deb,  libmateweather1-dbg_1.12.1-1_amd64.deb,  libmateweather-common_1.12.1-1_all.deb and  libmateweather-dev_1.12.1-1_amd64.deb.

Install the main lib package you just compiled (sudo dpkg -i libmateweather1_1.12.1-1_amd64.deb). If this does not work, try typing "cd .." and then "sudo dpkg -i libmateweather1_1.12.1-1_amd64.deb"

---

### Post by 894532185610544562 on 2016-09-10
Why would you do this over simply downloading and compiling [the latest official release]("https://github.com/mate-desktop/libmateweather/releases/tag/libmateweather-1.15.1")? Which btw, has the weather patches and [secure outgoing connections]("https://github.com/mate-desktop/libmateweather/commit/c1b71893ec34a2d0ea8f85ce7f30f536f8582123"), versus the old plaintext connections.

---

