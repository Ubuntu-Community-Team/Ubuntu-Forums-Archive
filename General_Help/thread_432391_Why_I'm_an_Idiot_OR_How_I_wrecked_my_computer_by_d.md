---
title: "Why I'm an Idiot OR How I wrecked my computer by deleting empty directories"
date: 2007-05-04
forum: General Help
---

### Post by mlissner on 2007-05-04
So, I had all these empty directories in my Music directory, so I wrote a script to delete them all. It worked well. In fact, it worked so well that I decided to see what would happen if I ran it on my entire home directory. This also worked well, except that apparently there are about 100 empty (vital) directories in my configuration files, which, for one moment and one moment alone, I forgot were in my home directory.

So. Those directories, and indeed any empty files that were there got deleted. I know because my script was designed to keep this log of the things it deleted:
```
/home/mlissner/.gconf/desktop/gnome/accessibility/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/peripherals/keyboard/host-opal/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/peripherals/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/url-handlers/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/screen/default/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/screen/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/applications/%gconf.xml
/home/mlissner/.gconf/desktop/gnome/connected_servers/%gconf.xml
/home/mlissner/.gconf/desktop/%gconf.xml
/home/mlissner/.gconf/apps/panel/applets/%gconf.xml
/home/mlissner/.gconf/apps/panel/applets/applet_3/%gconf.xml
/home/mlissner/.gconf/apps/panel/%gconf.xml
/home/mlissner/.gconf/apps/panel/objects/%gconf.xml
/home/mlissner/.gconf/apps/panel/toplevels/%gconf.xml
/home/mlissner/.gconf/apps/%gconf.xml
/home/mlissner/.gconf/apps/metacity/%gconf.xml
/home/mlissner/.gconf/apps/file-roller/%gconf.xml
/home/mlissner/.gconf/apps/file-roller/dialogs/%gconf.xml
/home/mlissner/.gconf/apps/GnomeBaker/Devices/%gconf.xml
/home/mlissner/.gconf/apps/gnome-settings/%gconf.xml
/home/mlissner/.gconf/apps/gedit-2/preferences/ui/%gconf.xml
/home/mlissner/.gconf/apps/gedit-2/preferences/%gconf.xml
/home/mlissner/.gconf/apps/gedit-2/%gconf.xml
/home/mlissner/.gconf/apps/gnome-terminal/profiles/%gconf.xml
/home/mlissner/.gconf/apps/gnome-terminal/%gconf.xml
/home/mlissner/.gconf/apps/gnome_settings_daemon/%gconf.xml
/home/mlissner/.gconf/apps/screem/%gconf.xml
/home/mlissner/.gconf/apps/gthumb/%gconf.xml
/home/mlissner/.gconf/apps/gthumb/dialogs/%gconf.xml
/home/mlissner/.gconf/apps/ekiga/%gconf.xml
/home/mlissner/.gconf/apps/ekiga/devices/%gconf.xml
/home/mlissner/.gconf/apps/ekiga/general/user_interface/%gconf.xml
/home/mlissner/.gconf/apps/ekiga/codecs/%gconf.xml
/home/mlissner/.gconf/apps/gnome-session/%gconf.xml
/home/mlissner/.gconf/apps/gok/%gconf.xml
/home/mlissner/.gconf/apps/gswitchit/%gconf.xml
/home/mlissner/.gconf/apps/eog/%gconf.xml
/home/mlissner/.gconf/apps/f-spot/%gconf.xml
/home/mlissner/.gconf/apps/workrave/gui/breaks/%gconf.xml
/home/mlissner/.gconf/apps/workrave/gui/%gconf.xml
/home/mlissner/.gconf/apps/workrave/%gconf.xml
/home/mlissner/.gconf/apps/workrave/timers/%gconf.xml
/home/mlissner/.gconf/apps/gnucash/dialogs/%gconf.xml
/home/mlissner/.gconf/apps/gnucash/%gconf.xml
/home/mlissner/.gconf/apps/gnucash/window/pages/%gconf.xml
/home/mlissner/.gconf/apps/gnucash/window/%gconf.xml
/home/mlissner/.gconf/apps/gnucash/general/warnings/%gconf.xml
/home/mlissner/.gconf/apps/gnucash/general/%gconf.xml
/home/mlissner/.gconf/apps/baobab/%gconf.xml
/home/mlissner/.gconf/system/gstreamer/0.10/%gconf.xml
/home/mlissner/.gconf/system/gstreamer/%gconf.xml
/home/mlissner/.gconf/system/%gconf.xml
/home/mlissner/.gconf/system/networking/wireless/networks/%gconf.xml
/home/mlissner/.gconf/system/networking/wireless/%gconf.xml
/home/mlissner/.gconf/system/networking/%gconf.xml
/home/mlissner/.gconf/schemas/apps/%gconf.xml
/home/mlissner/.gconf/schemas/apps/workspace_switcher_applet/%gconf.xml
/home/mlissner/.gconf/schemas/%gconf.xml
/home/mlissner/.gnome2/nautilus-scripts
/home/mlissner/.gnome2/file-roller
/home/mlissner/.gnome2/gthumb/comments
/home/mlissner/.gnome2/gthumb/bookmarks
/home/mlissner/.gnome2/gthumb/remote_cache
/home/mlissner/.gnome2/gnome-dictionary
/home/mlissner/.gnome2/deskbar-applet/handlers
/home/mlissner/.gnome2_private
/home/mlissner/.mozilla/firefox/gjeq8uyv.default/.parentlock
/home/mlissner/.mozilla/firefox/gjeq8uyv.default/extensions/{e4a8a97b-f2ed-450b-b12d-ee082ba24781}/chrome/chromeFiles/content/MochiKit
/home/mlissner/.mozilla/firefox/gjeq8uyv.default/chatzilla/scripts
/home/mlissner/.mozilla/firefox/gjeq8uyv.default/chatzilla/logs
/home/mlissner/.mozilla/firefox/gjeq8uyv.default/chatzilla/downloads
/home/mlissner/.gksu.lock
/home/mlissner/.sudo_as_admin_successful
/home/mlissner/.thumbnails/large
/home/mlissner/.icons
/home/mlissner/InstallFiles/easyubuntu/EasyUbuntu/__init__.py
/home/mlissner/InstallFiles/InstallFiles - Fedora/rockbox/unzipped/.rockbox/backdrops
/home/mlissner/InstallFiles/madwifi-0.9.2.1/ath/.ah_osdep.o.d
/home/mlissner/InstallFiles/madwifi-0.9.2.1/svnversion.h
/home/mlissner/InstallFiles/madwifi-0.9.2.1/.tmp_versions
/home/mlissner/InstallFiles/pam_keyring-0.0.8/FAQ
/home/mlissner/InstallFiles/DamnSmallLinux/syslinux-3.36/com32/include/time.h
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/VMware/VmPerl/.exists
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/VMware/VmPerl/VmPerl.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/VMware/VmdbPerl/.exists
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/VMware/VmdbPerl/VmdbPerl.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/VMware/HConfig/.exists
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/VMware/HConfig/HConfig.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/XML/Parser/Expat/Expat.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/MIME/Base64/Base64.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/auto/Authen/PAM/PAM.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/i386-linux/VMware/.exists
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/auto/IO/IO.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/auto/Socket/Socket.bs
/home/mlissner/InstallFiles/vmware-server-distrib/lib/perl5/site_perl/5.005/auto/POSIX/POSIX.bs
/home/mlissner/InstallFiles/vmware-server-distrib/etc/not_configured
/home/mlissner/.gaim/smileys
/home/mlissner/.gpilotd
/home/mlissner/Documents/Politcal/Archival/Gold Student Center Restaurant/Student.wpd
/home/mlissner/vmware/winxp.vmsd
/home/mlissner/vmware/WindowsXPPro.vmsd
/home/mlissner/.beagle/Indexes/EvolutionDataServerIndex/Locks
/home/mlissner/.beagle/Indexes/EvolutionDataServerIndex/Photos
/home/mlissner/.beagle/Indexes/EvolutionMailIndex/Locks
/home/mlissner/.beagle/Indexes/KMailIndex/Locks
/home/mlissner/.beagle/Indexes/FileSystemIndex/Locks
/home/mlissner/.beagle/Indexes/GaimLogIndex/Locks
/home/mlissner/.beagle/Indexes/IndexingServiceIndex/Locks
/home/mlissner/.beagle/Indexes/TomboyIndex/Locks
/home/mlissner/.beagle/Indexes/BlamIndex/Locks
/home/mlissner/.beagle/Indexes/LifereaIndex/Locks
/home/mlissner/.beagle/Indexes/AkregatorIndex/Locks
/home/mlissner/.beagle/Indexes/KonqHistoryIndex/Locks
/home/mlissner/.beagle/Indexes/KopeteIndex/Locks
/home/mlissner/.beagle/Indexes/ThunderbirdIndex/Locks
/home/mlissner/.beagle/Indexes/LabyrinthIndex/Locks
/home/mlissner/.beagle/Indexes/KonqBookmarkIndex/Locks
/home/mlissner/.beagle/Indexes/KNotesIndex/Locks
/home/mlissner/.beagle/Indexes/KOrganizerIndex/Locks
/home/mlissner/.beagle/Indexes/KAddressBookIndex/Locks
/home/mlissner/.beagle/Indexes/KonversationIndex/Locks
/home/mlissner/.beagle/TextCache/04/927a35-96fd-48e5-8bf1-c1de4acade56
/home/mlissner/.beagle/TextCache/06/3cc9f1-6580-4393-b9cc-946d837fda0f
/home/mlissner/.beagle/TextCache/08/112408-e82b-48e2-9528-89c4d670e0a7
/home/mlissner/.beagle/TextCache/0f/863e38-dd86-4e60-bed7-b2b5e5c424f1
/home/mlissner/.beagle/TextCache/25/04c6c9-b0cc-4f3f-8b12-a0592c6d6be9
/home/mlissner/.beagle/TextCache/2c/11b9c1-169c-4a96-83ed-8b425078a2f4
/home/mlissner/.beagle/TextCache/38/322076-707d-448f-b131-8525cbe857a0
/home/mlissner/.beagle/TextCache/3e/d4cdcd-8e61-42f8-906d-9eb70ecd3306
/home/mlissner/.beagle/TextCache/42/fd6a0e-3b11-4a65-9d65-225774de6e77
/home/mlissner/.beagle/TextCache/49/319990-3bd0-44cb-af06-f48e3974ca74
/home/mlissner/.beagle/TextCache/50/ac3da2-bc95-4041-acc0-3aeebc94d9fa
/home/mlissner/.beagle/TextCache/52/7dee73-d123-4ee0-a44b-fbab16ca7723
/home/mlissner/.beagle/TextCache/53/46f00e-93d2-416b-9812-2aadbd7445b6
/home/mlissner/.beagle/TextCache/54/d6d8f7-ed9c-46a5-a66c-9bc94abe3973
/home/mlissner/.beagle/TextCache/5e/56dba3-f6d6-49e5-a4c9-21e9b5382d8d
/home/mlissner/.beagle/TextCache/74/fbd85f-44b2-470a-8c4a-c0a2972b2b91
/home/mlissner/.beagle/TextCache/97/f20215-9bb3-40c5-8ffb-453b9c457379
/home/mlissner/.beagle/TextCache/9b/ebeddd-686a-4420-a8dd-69cf2b24e264
/home/mlissner/.beagle/TextCache/ae/6e09fd-2e4d-4f19-a960-0173acc36f10
/home/mlissner/.beagle/TextCache/be/e02fb7-b8df-44d5-b29a-3169624b3c15
/home/mlissner/.beagle/TextCache/d0/a8a8bc-4829-4b8d-a3c7-60c30511c2f7
/home/mlissner/.beagle/TextCache/d6/417930-9582-485f-a5bc-e7d5673d5074
/home/mlissner/.beagle/TextCache/e1/16fe2c-58ea-495f-8328-7dd473e47744
/home/mlissner/.beagle/TextCache/e9/b870da-b84b-4804-afba-9e14c619c9a3
/home/mlissner/.beagle/TextCache/ee/d90f7d-3c85-487b-b599-3052fbd3bac3
/home/mlissner/.beagle/TextCache/f0/085182-9697-4139-8ea8-1d6f188cd4cd
/home/mlissner/.beagle/ToIndex
/home/mlissner/.openoffice.org2/user/config/imagecache
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/swriter/menubar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/swriter/toolbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/swriter/statusbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/swriter/images/Bitmaps
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/scalc/menubar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/scalc/toolbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/scalc/statusbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/scalc/images/Bitmaps
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/sweb/menubar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/sweb/toolbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/sweb/statusbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/StartModule/menubar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/StartModule/toolbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/StartModule/statusbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/StartModule/images/Bitmaps
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/dbapp/menubar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/dbapp/toolbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/dbapp/statusbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/dbapp/images/Bitmaps
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/simpress/menubar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/simpress/toolbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/simpress/statusbar
/home/mlissner/.openoffice.org2/user/config/soffice.cfg/modules/simpress/images/Bitmaps
/home/mlissner/.openoffice.org2/user/Scripts
/home/mlissner/.openoffice.org2/user/autocorr
/home/mlissner/.openoffice.org2/user/backup
/home/mlissner/.openoffice.org2/user/psprint/driver
/home/mlissner/.openoffice.org2/user/psprint/fontmetric
/home/mlissner/.openoffice.org2/user/store
/home/mlissner/.openoffice.org2/user/temp
/home/mlissner/.openoffice.org2/user/template
/home/mlissner/.openoffice.org2/user/uno_packages/cache
/home/mlissner/.gdesklets/Displays
/home/mlissner/.gdesklets/Controls
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.googlemail.com/Drafts
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.googlemail.com/Templates
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.googlemail.com/Sent
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/Family
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/Claremont
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/Claremont.sbd/
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/Claremont.sbd/
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/Paypal.msf
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Inbox.sbd/Hiking
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Unsent Messages
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/Local Folders/Trash.sbd
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm.com/Inbox
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm.com/Drafts
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm.com/filterlog.html
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm.com/Templates
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm.com/Trash
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm.com/Sent
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.michaeljaylissner.com/Inbox
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.michaeljaylissner.com/Drafts
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.michaeljaylissner.com/Templates
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.michaeljaylissner.com/Trash
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/pop.michaeljaylissner.com/Sent
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-1.com/Inbox
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-1.com/Drafts
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-1.com/filterlog.html
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-1.com/Templates
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-1.com/Trash
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-1.com/Sent
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-2.com/Inbox
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-2.com/Trash
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-2.com/Sent
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-2.com/Drafts
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/Mail/mail.intercomm-2.com/Templates
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/extensions
/home/mlissner/.mozilla-thunderbird/c24fwcij.default/.parentlock
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.googlemail.com/Drafts
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.googlemail.com/Templates
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.googlemail.com/Sent
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.googlemail.com/Trash.msf
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Inbox.sbd/Family
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Inbox.sbd/Claremont
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Inbox.sbd/Claremont.sbd/
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Inbox.sbd/Berkeley.sbd/
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Inbox.sbd/Berkeley
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Inbox.sbd/San Diego
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Sent.msf
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Unsent Messages
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Trash.sbd
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Drafts.msf
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/Local Folders/Trash.msf
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm.com/Inbox
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm.com/Drafts
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm.com/filterlog.html
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm.com/Templates
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm.com/Trash
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm.com/Sent
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.michaeljaylissner.com/Inbox
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.michaeljaylissner.com/Drafts
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.michaeljaylissner.com/Templates
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.michaeljaylissner.com/Trash
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/pop.michaeljaylissner.com/Sent
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/News & Blogs/
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/News & Blogs/Trash.msf
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/News & Blogs/InfoMatters.msf
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/News & Blogs/
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/News & Blogs/
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm-1.com/Inbox
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm-1.com/Drafts
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm-1.com/filterlog.html
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm-1.com/Templates
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm-1.com/Trash
/home/mlissner/.mozilla-thunderbird/z33weijc/Mail/mail.intercomm-1.com/Sent
/home/mlissner/.mozilla-thunderbird/z33weijc/extensions
/home/mlissner/.mozilla-thunderbird/z33weijc/.parentlock
/home/mlissner/.bmp/Plugins
/home/mlissner/.java/deployment/tmp/si
/home/mlissner/.java/deployment/cache/javapi/v1.0/ext
/home/mlissner/.java/deployment/cache/javapi/v1.0/tmp
/home/mlissner/.java/deployment/cache/tmp
/home/mlissner/.java/deployment/ext
/home/mlissner/.dvdcss/NEW-2006041911340000
/home/mlissner/.dvdcss/PCT_MOVIE_TOTAL-2005092315582900
/home/mlissner/.dvdcss/-0daae3000dabce00-0009b1b800
/home/mlissner/.dvdcss/DVD_VR-2006112319470000
/home/mlissner/Websites/michaeljaylissner.com/natalie/assets/stylesheets
/home/mlissner/Websites/michaeljaylissner.com/county/assets/docs
/home/mlissner/Websites/michaeljaylissner.com/county/assets/images
/home/mlissner/Websites/michaeljaylissner.com/county/assets/spreadsheets
/home/mlissner/Websites/michaeljaylissner.com/county/assets/stylesheets
/home/mlissner/Websites/michaeljaylissner.com/county/assets/templates
/home/mlissner/Websites/michaeljaylissner.com/county/assets/videos
/home/mlissner/Websites/michaeljaylissner.com/assets/scripts/gmap
/home/mlissner/Websites/michaeljaylissner.com/archive/assets/images
/home/mlissner/Websites/michaeljaylissner.com/archive/assets/spreadsheets
/home/mlissner/Websites/charityhikers.org/assets/css
/home/mlissner/Websites/charityhikers.org/assets/images
/home/mlissner/Websites/charityhikers.org/assets/other
/home/mlissner/Websites/charityhikers.org/assets/spreadsheets
/home/mlissner/Websites/charityhikers.org/assets/worddocs
/home/mlissner/Websites/charityhikers.org/charityinfo/alzheimers
/home/mlissner/Websites/charityhikers.org/charityinfo/cancer
/home/mlissner/Websites/charityhikers.org/charityinfo/conservationnw
/home/mlissner/Websites/charityhikers.org/charityinfo/hogar
/home/mlissner/Websites/charityhikers.org/charityinfo/iavi
/home/mlissner/Websites/charityhikers.org/charityinfo/pcta
/home/mlissner/.mplayer/gui.url
/home/mlissner/.mplayer/gui.history
/home/mlissner/.qt/.qt_plugins_3.3rc.lock
/home/mlissner/.qt/.qtrc.lock
/home/mlissner/.qt/.kconfigrc.lock
/home/mlissner/.kde/share/servicetypes
/home/mlissner/.kde/share/apps/amarok/collection_scan.files
/home/mlissner/.kde/share/apps/amarok/scripts-data/KoverSS/final
/home/mlissner/.kde/share/apps/amarok/moods
/home/mlissner/.kde/share/apps/amarok/magnatune.com/purchases
/home/mlissner/.kde/share/apps/konqueror/bookmarks.xml.tbcache
/home/mlissner/.kde/share/apps/kfm/bookmarks
/home/mlissner/.kde/share/apps/kwallet
/home/mlissner/.kde/share/apps/kopete/contactlist.xml
/home/mlissner/.kde/share/apps/kdesktop
/home/mlissner/.kde/share/apps/kicker/extensions
/home/mlissner/.kde/share/apps/kicker/applets
/home/mlissner/.kde/share/apps/kabc/std.vcf
/home/mlissner/.kde/share/apps/kabc/lock
/home/mlissner/.kde/share/apps/kabc/std.vcf__0
/home/mlissner/.kde/share/apps/remoteview
/home/mlissner/.kde/share/apps/keep
/home/mlissner/.kde/share/apps/kmail/mail/inbox/new
/home/mlissner/.kde/share/apps/kmail/mail/inbox/cur
/home/mlissner/.kde/share/apps/kmail/mail/inbox/tmp
/home/mlissner/.kde/share/apps/kmail/mail/outbox/new
/home/mlissner/.kde/share/apps/kmail/mail/outbox/cur
/home/mlissner/.kde/share/apps/kmail/mail/outbox/tmp
/home/mlissner/.kde/share/apps/kmail/mail/sent-mail/new
/home/mlissner/.kde/share/apps/kmail/mail/sent-mail/cur
/home/mlissner/.kde/share/apps/kmail/mail/sent-mail/tmp
/home/mlissner/.kde/share/apps/kmail/mail/trash/new
/home/mlissner/.kde/share/apps/kmail/mail/trash/cur
/home/mlissner/.kde/share/apps/kmail/mail/trash/tmp
/home/mlissner/.kde/share/apps/kmail/mail/drafts/new
/home/mlissner/.kde/share/apps/kmail/mail/drafts/cur
/home/mlissner/.kde/share/apps/kmail/mail/drafts/tmp
/home/mlissner/.kde/share/apps/kmail/imap
/home/mlissner/.kde/share/apps/kmail/dimap
/home/mlissner/.kde/share/apps/kmail/search
/home/mlissner/.kde/share/apps/kab
/home/mlissner/.kde/share/apps/koffice
/home/mlissner/.kde/share/apps/khelpcenter/index
/home/mlissner/.kde/share/apps/ScanImages
/home/mlissner/.kde/share/apps/drkonqi
/home/mlissner/.kde/share/apps/konsole
/home/mlissner/.kde/share/apps/kfile
/home/mlissner/.kde/share/apps/k3b/temp
/home/mlissner/.kde/share/apps/kssl
/home/mlissner/.kde/share/locale
/home/mlissner/.scim
/home/mlissner/.screem/helpers
/home/mlissner/.screem/dtds
/home/mlissner/.picasa/drive_c/Program Files/Picasa2/mp3
/home/mlissner/.picasa/drive_c/Program Files/Common Files
/home/mlissner/.picasa/drive_c/windows/temp/Picasa2/Picasa filecheck
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Local Settings/Temporary Internet Files
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Local Settings/History
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Local Settings/Application Data/Google/Picasa2/tmp
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Local Settings/Application Data/Google/Picasa2/db/starlist.txt
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Local Settings/Application Data/Google/Picasa2/Desktop
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Local Settings/Application Data/Google/Picasa2Albums/0e4ae39e4eaf326278c09803376cf8cf
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Cookies
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Start Menu/Programs/StartUp
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Favorites
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Application Data
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Recent
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/SendTo
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/NetHood
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/Templates
/home/mlissner/.picasa/drive_c/Documents and Settings/mlissner/PrintHood
/home/mlissner/.picasa/drive_c/Documents and Settings/All Users/Start Menu/Programs/StartUp
/home/mlissner/.picasa/drive_c/Documents and Settings/All Users/Desktop
/home/mlissner/.picasa/drive_c/Documents and Settings/All Users/Favorites
/home/mlissner/.picasa/drive_c/Documents and Settings/All Users/Application Data
/home/mlissner/.picasa/drive_c/Documents and Settings/All Users/Templates
/home/mlissner/.picasa/drive_c/Documents and Settings/All Users/Documents
/home/mlissner/.adobe/Acrobat/7.0/Preferences/Collab/Temp
/home/mlissner/.adobe/Acrobat/7.0/Temp
/home/mlissner/bin/FoldingAtHome/work/wudata_01.dyn
/home/mlissner/bin/FoldingAtHome/work/wudata_01.goe
/home/mlissner/bin/FoldingAtHome/work/wudata_01.arc
/home/mlissner/bin/FoldingAtHome/work/wudata_01.sas
/home/mlissner/bin/FoldingAtHome/work/wudata_01.pdo
/home/mlissner/bin/FoldingAtHome/work/wudata_01.xvg
/home/mlissner/.juniper_networks/network_connect/missing.info
/home/mlissner/.evolution/calendar/config
/home/mlissner/.evolution/tasks/config
/home/mlissner/.evolution/memos/config
/home/mlissner/.evolution/cache
/home/mlissner/.evolution/mail/local/Inbox.ibex.index.data
/home/mlissner/.evolution/mail/local/Drafts
/home/mlissner/.evolution/mail/local/Outbox
/home/mlissner/.evolution/mail/local/Drafts.ibex.index.data
/home/mlissner/.evolution/mail/local/Sent
/home/mlissner/.evolution/mail/local/Outbox.ibex.index.data
/home/mlissner/.evolution/mail/local/Sent.ibex.index.data
/home/mlissner/.filezilla/lockfile
/home/mlissner/.ies4linux/ie6/drive_c/windows/system32/drivers
/home/mlissner/.ies4linux/ie6/drive_c/windows/temp
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/Start Menu/Programs/StartUp
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/Favorites/Links
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/Application Data/Microsoft/SystemCertificates/My/Certificates
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/Application Data/Microsoft/SystemCertificates/My/CRLs
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/Application Data/Microsoft/SystemCertificates/My/CTLs
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/Recent
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/SendTo
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/NetHood
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/Templates
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/PrintHood
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/UserData/WOGQ9JKU
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/UserData/4NF780ST
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/UserData/85IF8TEZ
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/mlissner/UserData/8HMB4LER
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/All Users/Desktop
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/All Users/Favorites
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/All Users/Application Data
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/All Users/Templates
/home/mlissner/.ies4linux/ie6/drive_c/windows/profiles/All Users/Documents
/home/mlissner/.ies4linux/ie6/drive_c/Program Files/Common Files
/home/mlissner/.local/share/mime/subclasses
/home/mlissner/.local/share/mime/XMLnamespaces
/home/mlissner/.local/share/mime/aliases
/home/mlissner/.tsclient/mru.tsc
/home/mlissner/.fonts
/home/mlissner/.wine/drive_c/windows/fonts
/home/mlissner/.wine/drive_c/windows/system
/home/mlissner/.wine/drive_c/windows/system32/drivers
/home/mlissner/.wine/drive_c/windows/temp
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Local Settings/Temporary Internet Files
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Local Settings/History
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Local Settings/Application Data
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Cookies
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Start Menu/Programs/StartUp
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Favorites
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Application Data
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Recent
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/SendTo
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/NetHood
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/Templates
/home/mlissner/.wine/drive_c/windows/profiles/mlissner/PrintHood
/home/mlissner/.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/StartUp
/home/mlissner/.wine/drive_c/windows/profiles/All Users/Desktop
/home/mlissner/.wine/drive_c/windows/profiles/All Users/Favorites
/home/mlissner/.wine/drive_c/windows/profiles/All Users/Application Data
/home/mlissner/.wine/drive_c/windows/profiles/All Users/Templates
/home/mlissner/.wine/drive_c/windows/profiles/All Users/Documents
/home/mlissner/.wine/drive_c/Program Files/Common Files
/home/mlissner/.azureus/.lock
/home/mlissner/.azureus/tmp/AZU5177.tmp
/home/mlissner/.azureus/plugins
/home/mlissner/.azureus/shares
/home/mlissner/.azureus/ipfilter.cache
/home/mlissner/.azureus/updates
/home/mlissner/.gimp-2.2/brushes
/home/mlissner/.gimp-2.2/fonts
/home/mlissner/.gimp-2.2/gradients
/home/mlissner/.gimp-2.2/palettes
/home/mlissner/.gimp-2.2/patterns
/home/mlissner/.gimp-2.2/plug-ins
/home/mlissner/.gimp-2.2/modules
/home/mlissner/.gimp-2.2/environ
/home/mlissner/.gimp-2.2/scripts
/home/mlissner/.gimp-2.2/templates
/home/mlissner/.gimp-2.2/themes
/home/mlissner/.gimp-2.2/tmp
/home/mlissner/.gimp-2.2/curves
/home/mlissner/.gimp-2.2/levels
/home/mlissner/.gimp-2.2/fractalexplorer
/home/mlissner/.gimp-2.2/gfig
/home/mlissner/.gimp-2.2/gflare
/home/mlissner/.gimp-2.2/gimpressionist
/home/mlissner/.frostwire/xml/data/delete_me
/home/mlissner/.xmms/Skins
/home/mlissner/.xmms/Plugins
/home/mlissner/.easytag/scan_tag.mask
/home/mlissner/.easytag/rename_directory.mask
/home/mlissner/.easytag/browser_path.history
/home/mlissner/.easytag/play_list_name.mask
/home/mlissner/.easytag/run_program_with_directory.history
/home/mlissner/.easytag/run_program_with_file.history
/home/mlissner/.easytag/search_file.history
/home/mlissner/.easytag/file_to_load.history
/home/mlissner/.easytag/playlist_content.mask
/home/mlissner/.easytag/cddb_search_string.history
/home/mlissner/.easytag/cddb_search_string_in_result.history
/home/mlissner/.synaptic/options
/home/mlissner/.opera/lock
/home/mlissner/.opera/widgets/xiepqalnqiibtqaxglduuuvjhlpypl/cache
/home/mlissner/.loki/installed/locale
/home/mlissner/.googleearth/Registry/google/googleearthplus/User/customcobrandpath
/home/mlissner/.googleearth/Registry/google/googleearthplus/User/hiddenwindows
/home/mlissner/.googleearth/Cache/models
/home/mlissner/.googleearth/Cache/images
/home/mlissner/.gnucash/expressions-2.0
/home/mlissner/Accounting/Personal Finance.7f0100.13222.LNK
/home/mlissner/.lineak/Pics
/home/mlissner/.xchat2/downloads
/home/mlissner/.xchat2/sound.conf
/home/mlissner/.xchat2/notify.conf
/home/mlissner/.xchat2/ignore.conf
/home/mlissner/.tomboy/Plugins
/home/mlissner/.dvdrip-data
```

So, those files seemed to have been deleted, and suddenly my computer didn't do things it used to do fine. Thinking on my feet, I decided to create a script to read that log and make a directory for each of those that had been deleted. I made that script, but when I ran it, it said that all of those files already existed. Strange indeed.

Anyway, have I blown it for good, or does anybody have any brilliant ideas for a fix? Here's the script that did the damage:
```
#!/bin/bash
# Name: rmempty.sh
# Purpose: To remove empty files and directories from a path
# Author: MLissner
# Date: 2-17-07


clear
echo 'Welcome to the rmempty.sh script.'
echo -n 'Please enter the directory you wish to search in: '
read searchdir

if [ -d $searchdir ]
then
  sleep 1
else
  echo rmempty.sh: invalid directory. Exiting.
  exit 1
fi

#Create a place to move things.
if [ -d ~/.Trash/rmempty ]
then
  echo -n '~/.Trash/rmempty exists. Do you wish to continue (y/n): '
  read yesno
  if [ $yesno = y ]
  then
    echo Ok. You should be ok. You will be prompted for confirmation before any files are overwritten.
  else
    echo OK. Exiting.
    exit 1
  fi
else
  mkdir ~/.Trash/rmempty
fi

echo
echo Proceeding with checks...
sleep 1
echo


#create and update the log
$count=`find $searchdir -empty | wc -l`
echo '###########' >> ~/.Trash/rmempty/rmempty.log
date >> ~/.Trash/rmempty/rmempty.log
find $searchdir -empty >> ~/.Trash/rmempty/rmempty.log

#do the work in one swift movement
find $searchdir -empty -print0 | xargs -0 rm -rf

sleep 2
echo The following $count files have been moved to ~/.Trash/rmempty
more ~/.Trash/rmempty/rmempty.log
echo
echo This log is located at ~/.Trash/rmempty/rmempty.log
echo You may want to run this script another few times in case new empty directories have been created.
echo 
echo Goodbye.

exit 0
```

Any help is appreciated. Thanks.

---

### Post by yopnono on 2007-05-04
If you only run it in the home folder your system is ok. And the folders/files you removed are created on login again. You can create a new login profile, and then login to and try and see if the machine is working like it should.

Then  copy your stuff from the old profile to the new one, then remove that home folder (the old) and make a copy of the new home folder and then rename it to the old home folder name.

Or enable root login and try that account. From the root account you can *rename* the old home folder and remove the old profile, then create a new profile with the old name you use to have, then just copy the stuff you like to keep from the old home folder that you renamed to the newly created home folder. 

Hope you get it ;)

---

### Post by mlissner on 2007-05-05
I started by creating a new profile, which got me back online when I eventualyl rebooted, but actually I'm having pretty good success with renaming the hidden directories in my current home directory so they get rebuilt the next time the program is run. So far, that's worked for the gnome, openoffice, and beryl directories. 

One place I may be in a lot of pain though is in my .mozilla-thunderbird directory, which simply won't open. I tried opening it in the terminal, but no errors are reported - it just doesn't work, which means that all my old mail and such is gone for the moment. I'm going through the log of deleted directories and files and trying to figure out which vital thing is missing, but this could take quite a while.

Any other brilliant ideas on this would be helpful.

---

### Post by yopnono on 2007-05-05
What do you mean it don't open? What happens if you unhide the folders and just open the .mozilla-thunderbird folder. Or if you do a ls -la in the shell or cd in to it.

---

### Post by mlissner on 2007-05-05
Actually, let me rephrase. The directory seems to be fine. I even just checked the log above vs the contents of the directory to see if there were any missing directories or files (there weren't). The problem I'm having is that Thunderbird itself won't open. I can create new profiles and they open fine via the profile manager, but I can't open either of my two old profiles, which means my address book, mail etc. is all suddenly gone. When I try to open Thunderbird, it just tries to open and gives up. Same thing if I do it via terminal.

I tried opening evolution and importing the profile, but that too fails (apparently evolution can't do thunderbird profiles, surprise surprise).

Thanks again.

---

### Post by mlissner on 2007-05-05
Well, I've recovered my thunderbird settings, though it wasn't easy. Essentially, what I did was create a new profile using the profile manager and then move the files over from the old profile one by one, rebuilding cautiously.

I think I got everything moved over aside from a few minor things like my junkmail history. I wish I could have figured out what broke in the old profile, thus fixing it, but I think this was the easiest way to take care of business.

I'll post for posterity if I find any other programs that I killed. At the moment though, I think I've got my computer back.

Thanks for the help.

---

### Post by Ripfox on 2007-05-28
I'm sorry, but lol...you wrote a script to mess up your own computer. I'm laughing with you buddy...geez, what a kick in the teeth! Sounds like a re-install.

---

### Post by mlissner on 2007-05-28
Indeed. Pretty stupid, I know. 

Just as an update for all of you out there that do similiarly idiotic things, my computer is alive and well sans reinstall. Once my profile in thunderbird was fixed, I fixed one or two other .program files, and all was well. The major ones I fixed were thunderbird and beryl. Other than that, all was well. 

It was an annoying time though...annoying and idiotic.

---

### Post by Ripfox on 2007-05-29
One time I deleted all the users not knowing they were there for a reason...I was like "who are these people?!?" 

So don't feel too bad, that BORKED my Ubuntu...

---

