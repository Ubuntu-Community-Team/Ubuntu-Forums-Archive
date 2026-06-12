---
title: "Digikam installation issues"
date: 2024-07-10
forum: General Help
---

### Post by ian-r-ashworth on 2024-07-10
Hi,
I have recently updated from Ubuntu 22.04LTS to 24.04LTS using the CLI and am still trying to get used to the differences.  I have tried to install digikam 8.2.0 using the CLI
"sudo apt install digikam"  and it seemed to work great, no error messages on install which ended as usual with the command prompt. Again from the CLI I tried to run digikam
"digikam" and it started asking for the location of the SQLite database files which I gave it.  "/home/ian/Pictures/larchive" in my system. It appeared to start fine but on inspection there were several Albums missing which had been there in ubuntu 22.04LTS.
At this time my terminal gave me a message:
digikam.metaengine: ExifTool process cannot be started ( "" )
ALSA lib pcm_dsnoop.c:567:snd_pcm_dsnoop_open) unable to open slave
ALSA lib pcm_dmix.c:1000:snd_pcm_dmix_open) unable to open slave
ALSA lib pcm.c:2721:snd_pcm_open_noupdate) Unknown PCM cards.pcm.rear
ALSA lib pcm.c:2721:snd_pcm_open_noupdate) Unknown PCM cards.pcm.center_lfe
ALSA lib pcm.c:2721:snd_pcm_open_noupdate) Unknown PCM cards.pcm.side
ALSA lib pcm_dmix.c:1000:snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server request channel
jack server is not running or cannot be started
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
JackShmReadWritePtr::~JackShmReadWritePtr - Init not done for -1, skipping unlock
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
kf.sonnet.clients.hspell: HSpellDict::HSpellDict: Init failed
kf.xmlgui: Unhandled container to remove :  Digikam:digikamApp
The program will also not update its database with newly added photo's and albums. 
Please can anybody help with this?
Thanks in advance.
Ian

---

### Post by #&amp;thj^% on 2024-07-10
You really need more details for anyone to help, what cli do you use:
```
 digikam -qwindowtitle
Path override failed for key base::DIR_APP_DICTIONARIES and path '/usr/bin/qtwebengine_dictionaries'
Path override failed for key base::DIR_APP_DICTIONARIES and path '/usr/lib/qt6/qtwebengine_dictionaries'
Path override failed for key base::DIR_APP_DICTIONARIES and path '/usr/lib/qt6/qtwebengine_dictionaries'
kf.xmlgui: Unhandled container to remove :  Digikam::DigikamApp

```
You seem to be missing a dictionary can you show us this:
```
sudo find / -iname *hspell*
```
And check if it is installed if not install it:
```
sudo apt install hspell
```

Did you ever see a window that offered to download missing applications? Link: [https://docs.digikam.org/en/getting_started/quick_start.html](https://docs.digikam.org/en/getting_started/quick_start.html)
```
digikam --help
Usage: digikam [options]
Professional Photo Management with the Power of Open Source - A KDE Family Project

Options:
  -h, --help                  Displays help on commandline options.
  --help-all                  Displays help including Qt specific options.
  -v, --version               Displays version information.
  --author                    Show author information.
  --license                   Show license information.
  --desktopfile <file name>   The base file name of the desktop entry for this
                              application.
  --download-from <path>      Open camera dialog at "path"
  --download-from-udi <udi>   Open camera dialog for the device with Solid UDI
                              "udi"
  --detect-camera             Automatically detect and open a connected gphoto2
                              camera
  --database-directory <dir>  Start digikam with the SQLite database file found
                              in the directory "dir"
  --config <config>           Start digikam with the configuration file
                              "config"

```

After all said and done it should after the install look like:
```
Fetched 3,644 kB in 2s (1,634 kB/s)       
Selecting previously unselected package hunspell.
(Reading database ... 295312 files and directories currently installed.)
Preparing to unpack .../0-hunspell_1.7.2+really1.7.2-10build3_amd64.deb ...
Unpacking hunspell (1.7.2+really1.7.2-10build3) ...
Selecting previously unselected package libdbd-mysql-perl:amd64.
Preparing to unpack .../1-libdbd-mysql-perl_4.052-1ubuntu3_amd64.deb ...
Unpacking libdbd-mysql-perl:amd64 (4.052-1ubuntu3) ...
Selecting previously unselected package mariadb-common.
Preparing to unpack .../2-mariadb-common_1%3a11.4.2-3_all.deb ...
Unpacking mariadb-common (1:11.4.2-3) ...
Selecting previously unselected package libmariadb3:amd64.
Preparing to unpack .../3-libmariadb3_1%3a11.4.2-3_amd64.deb ...
Unpacking libmariadb3:amd64 (1:11.4.2-3) ...
Selecting previously unselected package libconfig-inifiles-perl.
Preparing to unpack .../4-libconfig-inifiles-perl_3.000003-2_all.deb ...
Unpacking libconfig-inifiles-perl (3.000003-2) ...
Selecting previously unselected package mariadb-client-core.
Preparing to unpack .../5-mariadb-client-core_1%3a11.4.2-3_amd64.deb ...
Unpacking mariadb-client-core (1:11.4.2-3) ...
Selecting previously unselected package mariadb-client.
Preparing to unpack .../6-mariadb-client_1%3a11.4.2-3_amd64.deb ...
Unpacking mariadb-client (1:11.4.2-3) ...
Setting up libconfig-inifiles-perl (3.000003-2) ...
Setting up hunspell (1.7.2+really1.7.2-10build3) ...
Setting up mariadb-common (1:11.4.2-3) ...
update-alternatives: using /etc/mysql/mariadb.cnf to provide /etc/mysql/my.cnf (
my.cnf) in auto mode
Setting up libdbd-mysql-perl:amd64 (4.052-1ubuntu3) ...
Setting up libmariadb3:amd64 (1:11.4.2-3) ...
Setting up mariadb-client-core (1:11.4.2-3) ...
Setting up mariadb-client (1:11.4.2-3) ...
Processing triggers for man-db (2.12.1-2) ...
Processing triggers for menu (2.1.50) ...
Processing triggers for libc-bin (2.39-0ubuntu9) ...

```
And now 
```
digikam -qwindowtitle
digikam.metaengine: ExifTool process cannot be started ( "" )
Hspell: can't open /usr/share/hspell/hebrew.wgz.sizes.
kf.sonnet.clients.hspell: HSpellDict::HSpellDict: Init failed
kf.xmlgui: Unhandled container to remove :  Digikam::DigikamApp
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap
QPixmap::scaled: Pixmap is a null pixmap

```
I'm on 24.10 Devel...
```
 apt policy digikam
digikam:
  Installed: 4:8.3.0-2ubuntu2
  Candidate: 4:8.3.0-2ubuntu2
  Version table:
 *** 4:8.3.0-2ubuntu2 500
        500 http://archive.ubuntu.com/ubuntu oracular/universe amd64 Packages
        100 /var/lib/dpkg/status

```

---

