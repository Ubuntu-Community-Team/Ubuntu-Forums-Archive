---
title: "Boot (/) partition too full - frightenerd to reboot"
date: 2008-03-04
forum: General Help
---

### Post by dryder on 2008-03-04
Hi,
Feisty

My Boot partition (/) is a whopping 37GB and this morning reached 100%! It now has only 3GB left after cleaning out the garbage bin.

I, like others as per this and following posts [[COLOR="Blue"]**here**[/COLOR]]("http://ubuntuforums.org/showthread.php?p=1167492#post1167492") set up my partitions accordingly. Not 'the blame game' simply that we didn't know any better.

But to use up 37GB in /boot since Feisty was released with basically just 'the normal' apps seems to me excessive, even though I use Feisty all the time except for scanning. Oh, I also use efax, Virtual Box and Boinc but aren't they in my /home folder?

I am reluctant to reboot lest I have corrupted esential files. For example, terminal has lost recent commands when using the up/down arrow.

Can anybody please advise me on how I can resolve this problem bearing in mind I always install using the Alternate CD and don't have or know how to use the Desktop CD. Can resizing the partitions be done live?

Masny thanks,
David

---

### Post by cmnorton on 2008-03-04
First, try to get a live CD to boot your system; then you should be able to back stuff up before you do anything. You would back things up to a pen drive or large usb drive. If you do not have a live CD, then download the Ubuntu live CD, and if that does not work download the latest version of Knoppix and boot with that.

Once you back up your most important data, I'd use du and sort -- still booted with a live CD -- to locate your biggest chunks of data, like log-rotated log files or things you can afford to delete. Then, I'd delete those files.

If you boot with a live CD, don't forget to mount the drive that doesn't have much room.

---

### Post by dryder on 2008-03-04
Thanks cmnorton.

1. Apart from /home should I backup /boot as well (I only have /boot and /home)?

2. Simple Backup won't backup to my usb drive - don't know why - so is that a copy to usb? Everything?

3. > I'd use du and sort... This is the result of du now... before doing anything: ```
8       ./.gconf/apps/gnucash/general/warnings/permanent
12      ./.gconf/apps/gnucash/general/warnings
20      ./.gconf/apps/gnucash/general
8       ./.gconf/apps/gnucash/dialogs/tax_info
8       ./.gconf/apps/gnucash/dialogs/account
8       ./.gconf/apps/gnucash/dialogs/new_user
8       ./.gconf/apps/gnucash/dialogs/preferences
8       ./.gconf/apps/gnucash/dialogs/tip_of_the_day
8       ./.gconf/apps/gnucash/dialogs/scheduled_trans/transaction_list
8       ./.gconf/apps/gnucash/dialogs/scheduled_trans/since_last_run
8       ./.gconf/apps/gnucash/dialogs/scheduled_trans/transaction_editor
28      ./.gconf/apps/gnucash/dialogs/scheduled_trans
8       ./.gconf/apps/gnucash/dialogs/business/invoice
12      ./.gconf/apps/gnucash/dialogs/business
84      ./.gconf/apps/gnucash/dialogs
152     ./.gconf/apps/gnucash
8       ./.gconf/apps/gnome-search-tool/select
16      ./.gconf/apps/gnome-search-tool
8       ./.gconf/apps/glchess/new_game_dialog/black
8       ./.gconf/apps/glchess/new_game_dialog/white
20      ./.gconf/apps/glchess/new_game_dialog
28      ./.gconf/apps/glchess
8       ./.gconf/apps/aisleriot/rules
16      ./.gconf/apps/aisleriot
8       ./.gconf/apps/tomboy
8       ./.gconf/apps/gnotravex
8       ./.gconf/apps/compiz/general/allscreens/options
12      ./.gconf/apps/compiz/general/allscreens
16      ./.gconf/apps/compiz/general
20      ./.gconf/apps/compiz
8       ./.gconf/apps/gnibbles/preferences
12      ./.gconf/apps/gnibbles
8       ./.gconf/apps/nautilus/desktop
8       ./.gconf/apps/nautilus/preferences
24      ./.gconf/apps/nautilus
8       ./.gconf/apps/gnomine/geometry
16      ./.gconf/apps/gnomine
8       ./.gconf/apps/serpentine
8       ./.gconf/apps/gnome-settings/gnome-panel
8       ./.gconf/apps/gnome-settings/gnome-desktop-item-edit
8       ./.gconf/apps/gnome-settings/gedit
8       ./.gconf/apps/gnome-settings/gnome-search-tool
36      ./.gconf/apps/gnome-settings
8       ./.gconf/apps/gedit-2/plugins/filebrowser/on_load
12      ./.gconf/apps/gedit-2/plugins/filebrowser
20      ./.gconf/apps/gedit-2/plugins
8       ./.gconf/apps/gedit-2/preferences/print/page
12      ./.gconf/apps/gedit-2/preferences/print
8       ./.gconf/apps/gedit-2/preferences/editor/right_margin
8       ./.gconf/apps/gedit-2/preferences/editor/bracket_matching
8       ./.gconf/apps/gedit-2/preferences/editor/line_numbers
8       ./.gconf/apps/gedit-2/preferences/editor/current_line
36      ./.gconf/apps/gedit-2/preferences/editor
8       ./.gconf/apps/gedit-2/preferences/ui/statusbar
12      ./.gconf/apps/gedit-2/preferences/ui
64      ./.gconf/apps/gedit-2/preferences
88      ./.gconf/apps/gedit-2
8       ./.gconf/apps/gnome-volume-control/ui
12      ./.gconf/apps/gnome-volume-control
8       ./.gconf/apps/file-roller/general
8       ./.gconf/apps/file-roller/dialogs/extract
8       ./.gconf/apps/file-roller/dialogs/batch-add
20      ./.gconf/apps/file-roller/dialogs
8       ./.gconf/apps/file-roller/listing
8       ./.gconf/apps/file-roller/ui
48      ./.gconf/apps/file-roller
8       ./.gconf/apps/gnome-screenshot
8       ./.gconf/apps/sound-juicer
8       ./.gconf/apps/gnome-system-log
8       ./.gconf/apps/gnome-power-manager
8       ./.gconf/apps/nautilus-cd-burner/ubuntu-server
16      ./.gconf/apps/nautilus-cd-burner
8       ./.gconf/apps/baobab/ui
12      ./.gconf/apps/baobab
8       ./.gconf/apps/gnome-app-install
8       ./.gconf/apps/gnect
8       ./.gconf/apps/gcalctool
8       ./.gconf/apps/gfax/transport/efax
12      ./.gconf/apps/gfax/transport
8       ./.gconf/apps/gfax/general
24      ./.gconf/apps/gfax
8       ./.gconf/apps/same-gnome
8       ./.gconf/apps/evolution/shell/view_defaults/folder_bar
16      ./.gconf/apps/evolution/shell/view_defaults
24      ./.gconf/apps/evolution/shell
8       ./.gconf/apps/evolution/mail/format
8       ./.gconf/apps/evolution/mail/prompts
8       ./.gconf/apps/evolution/mail/notify
8       ./.gconf/apps/evolution/mail/message_window
8       ./.gconf/apps/evolution/mail/display/fonts
16      ./.gconf/apps/evolution/mail/display
8       ./.gconf/apps/evolution/mail/composer/view
16      ./.gconf/apps/evolution/mail/composer
72      ./.gconf/apps/evolution/mail
8       ./.gconf/apps/evolution/memos
8       ./.gconf/apps/evolution/addressbook/display
16      ./.gconf/apps/evolution/addressbook
8       ./.gconf/apps/evolution/calendar/memos
8       ./.gconf/apps/evolution/calendar/notify
8       ./.gconf/apps/evolution/calendar/date_navigator
8       ./.gconf/apps/evolution/calendar/display
8       ./.gconf/apps/evolution/calendar/tasks
48      ./.gconf/apps/evolution/calendar
8       ./.gconf/apps/evolution/tasks
184     ./.gconf/apps/evolution
8       ./.gconf/apps/ggv/printing
8       ./.gconf/apps/ggv/gtkgs
8       ./.gconf/apps/ggv/control
8       ./.gconf/apps/ggv/layout
8       ./.gconf/apps/ggv/coordinates
44      ./.gconf/apps/ggv
8       ./.gconf/apps/rhythmbox/plugins/artdisplay
8       ./.gconf/apps/rhythmbox/plugins/daap
8       ./.gconf/apps/rhythmbox/plugins/power-manager
8       ./.gconf/apps/rhythmbox/plugins/audiocd
8       ./.gconf/apps/rhythmbox/plugins/generic-player
8       ./.gconf/apps/rhythmbox/plugins/iradio
8       ./.gconf/apps/rhythmbox/plugins/visualizer
8       ./.gconf/apps/rhythmbox/plugins/cd-recorder
8       ./.gconf/apps/rhythmbox/plugins/ipod
8       ./.gconf/apps/rhythmbox/plugins/mmkeys
84      ./.gconf/apps/rhythmbox/plugins
8       ./.gconf/apps/rhythmbox/state/iradio
8       ./.gconf/apps/rhythmbox/state/library
8       ./.gconf/apps/rhythmbox/state/podcast
32      ./.gconf/apps/rhythmbox/state
8       ./.gconf/apps/rhythmbox/ui/library
16      ./.gconf/apps/rhythmbox/ui
140     ./.gconf/apps/rhythmbox
8       ./.gconf/apps/mail-notification/commands/new-mail
12      ./.gconf/apps/mail-notification/commands
8       ./.gconf/apps/mail-notification/popups/expiration
16      ./.gconf/apps/mail-notification/popups
8       ./.gconf/apps/mail-notification/ui/properties-dialog
12      ./.gconf/apps/mail-notification/ui
48      ./.gconf/apps/mail-notification
8       ./.gconf/apps/eog/window
8       ./.gconf/apps/eog/ui
20      ./.gconf/apps/eog
1636    ./.gconf/apps
8       ./.gconf/GNOME/Spell
12      ./.gconf/GNOME
1904    ./.gconf
564     ./my-backups
16      ./.vuescan
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/youtube.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/images.soapbox.msn.com/flash/soapbox1_1.swf
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/images.soapbox.msn.com/flash
16      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/images.soapbox.msn.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/video.google.com/googleplayer.swf
16      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/video.google.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/natalie.feedroom.com/techwebtv/showcase/Player.swf
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/natalie.feedroom.com/techwebtv/showcase
16      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/natalie.feedroom.com/techwebtv
20      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/natalie.feedroom.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.idg.com.au/vplayer/flvplayer_r3.swf
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.idg.com.au/vplayer
16      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.idg.com.au
4       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.time.com/time/widgets/qotd_v10.swf
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.time.com/time/widgets
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.time.com/time
16      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.time.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/agfa.com/oceania/images/tom_coope#/r_donna_strater_tcm86-20444.swf
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/agfa.com/oceania/images/tom_coope#
16      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/agfa.com/oceania/images
20      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/agfa.com/oceania
24      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/agfa.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.abc.net.au
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/wp.vizu.com
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.afr.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/uncutvideo.aol.com
20      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.youtube.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.microsoft.com/australia/office/newday/home_shell.swf
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.microsoft.com/australia/office/newday
16      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.microsoft.com/australia/office
20      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.microsoft.com/australia
24      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.microsoft.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.plugoo.com/plugoo.swf
12      ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/www.plugoo.com
8       ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF/bin.clearspring.com
224     ./.macromedia/Flash_Player/#SharedObjects/LN9WTSTF
228     ./.macromedia/Flash_Player/#SharedObjects
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#video.google.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#natalie.feedroom.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#images.soapbox.msn.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.plugoo.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.idg.com.au
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#youtube.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.microsoft.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.time.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.youtube.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#wp.vizu.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.afr.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#uncutvideo.aol.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#agfa.com
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#www.abc.net.au
8       ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys/#bin.clearspring.com
128     ./.macromedia/Flash_Player/macromedia.com/support/flashplayer/sys
132     ./.macromedia/Flash_Player/macromedia.com/support/flashplayer
136     ./.macromedia/Flash_Player/macromedia.com/support
140     ./.macromedia/Flash_Player/macromedia.com
372     ./.macromedia/Flash_Player
376     ./.macromedia
8       ./.glchess
8       ./.gnucash/books
36      ./.gnucash
4       ./.BitTornado/torrentcache
4       ./.BitTornado/piececache
12      ./.BitTornado/datacache
148     ./.BitTornado/icons
176     ./.BitTornado
4       ./faxout
65584   ./Desktop/WEDDING MIKE & SYLVIA
2676    ./Desktop/untitled folder/WEDDING MIKE & SYLVIA
44048   ./Desktop/untitled folder/WEDDING
348     ./Desktop/untitled folder/WEDDING - Rob & Carla's
47076   ./Desktop/untitled folder
4       ./Desktop/nrma/ps
4       ./Desktop/nrma/TempImg
15160   ./Desktop/nrma/TIF
4       ./Desktop/nrma/eps
30432   ./Desktop/nrma
90596   ./Desktop/PRIDE AND PREJUDICE
1544    ./Desktop/vuesca84.tgz_FILES/html
8548    ./Desktop/vuesca84.tgz_FILES
19040   ./Desktop/.Trash-david
215808  ./Desktop/WEDDING
122508  ./Desktop/TESS
1332    ./Desktop/WEDDING - Rob & Carla's
627124  ./Desktop
8       ./.qt
4       ./.kde/share/servicetypes
76      ./.kde/share/config
4       ./.kde/share/services
4       ./.kde/share/apps/kwallet
8       ./.kde/share/apps/kcookiejar
12      ./.kde/share/apps/kconf_update/log
16      ./.kde/share/apps/kconf_update
4       ./.kde/share/apps/k3b
4       ./.kde/share/apps/konqueror
4       ./.kde/share/apps/khtml
24      ./.kde/share/apps/ktorrent
68      ./.kde/share/apps
4       ./.kde/share/mimelnk
4       ./.kde/share/applnk
164     ./.kde/share
168     ./.kde
1428708 ./my-downloads
560     ./.mozilla/firefox/1dpnaump.default/adblockplus
12      ./.mozilla/firefox/1dpnaump.default/chrome
4368    ./.mozilla/firefox/1dpnaump.default/Cache
996     ./.mozilla/firefox/1dpnaump.default/bookmarkbackups
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/locale/en-US
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/locale
72      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/content/colorPicker
320     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/content
132     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/skin/classic
136     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome/skin
496     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/chrome
12      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/defaults/preferences
16      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/defaults
52      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/components
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/chrome/locale/en-US
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/chrome/locale
72      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/chrome/content/colorPicker
316     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/chrome/content
120     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/chrome/skin/classic
124     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/chrome/skin
480     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/chrome
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/pl-PL
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/sr-YU
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/de-DE
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/en-GB
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/zh-TW
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/nl-NL
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/mn-MN
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/ro-RO
44      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/uk-UA
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/cs-CZ
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/fr-FR
48      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/el-GR
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/ko-KR
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/sk-SK
48      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/ru-RU
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/ja-JP
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/ca-AD
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/pt-BR
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/fi-FI
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/pt-PT
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/ar
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/it-IT
28      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/zh-CN
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5/es-AR
840     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations/0.9.5
844     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2/translations
1328    ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/downbarff2
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/pl-PL
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/sr-YU
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/de-DE
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/en-GB
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/zh-TW
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/nl-NL
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/mn-MN
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ro-RO
44      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/uk-UA
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/cs-CZ
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/fr-FR
48      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/el-GR
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ko-KR
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/sk-SK
48      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ru-RU
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ja-JP
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ca-AD
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/pt-BR
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/fi-FI
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/pt-PT
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/ar
32      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/it-IT
28      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/zh-CN
36      ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6/es-AR
836     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations/0.9.6
840     ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}/translations
2748    ./.mozilla/firefox/1dpnaump.default/extensions/{D4DD63FA-01E4-46a7-B6B1-EDAB7D6AD389}
240     ./.mozilla/firefox/1dpnaump.default/extensions/{9D23D0AA-D8F5-11DA-B3FC-0928ABF316DD}/chrome
8       ./.mozilla/firefox/1dpnaump.default/extensions/{9D23D0AA-D8F5-11DA-B3FC-0928ABF316DD}/defaults/preferences
12      ./.mozilla/firefox/1dpnaump.default/extensions/{9D23D0AA-D8F5-11DA-B3FC-0928ABF316DD}/defaults
276     ./.mozilla/firefox/1dpnaump.default/extensions/{9D23D0AA-D8F5-11DA-B3FC-0928ABF316DD}
948     ./.mozilla/firefox/1dpnaump.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/chrome
8       ./.mozilla/firefox/1dpnaump.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults/preferences
12      ./.mozilla/firefox/1dpnaump.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/defaults
20      ./.mozilla/firefox/1dpnaump.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}/components
1000    ./.mozilla/firefox/1dpnaump.default/extensions/{d10d0bf8-f5b5-c8b4-a8b2-2b9879e08c5d}
4028    ./.mozilla/firefox/1dpnaump.default/extensions
19928   ./.mozilla/firefox/1dpnaump.default
19940   ./.mozilla/firefox
6904    ./.mozilla/plugins
26852   ./.mozilla
380     ./my-templates
232     ./.limewire/themes/GTK_theme
376     ./.limewire/themes
4       ./.limewire/.AppSpecialShare
3312    ./.limewire/.NetworkShare
28      ./.limewire/xml/schemas
24      ./.limewire/xml/misc
8       ./.limewire/xml/data
64      ./.limewire/xml
3972    ./.limewire
504     ./Old efax logs
536     ./.gstreamer-0.10
8       ./.serpentine
8       ./.mcop/trader-cache
16      ./.mcop
4       ./.gimp-2.2/themes
4       ./.gimp-2.2/gimpressionist
300     ./.gimp-2.2/tool-options
4       ./.gimp-2.2/patterns
4       ./.gimp-2.2/plug-ins
4       ./.gimp-2.2/templates
4       ./.gimp-2.2/scripts
4       ./.gimp-2.2/brushes
4       ./.gimp-2.2/gflare
4       ./.gimp-2.2/modules
4       ./.gimp-2.2/palettes
4       ./.gimp-2.2/environ
4       ./.gimp-2.2/levels
4       ./.gimp-2.2/curves
4       ./.gimp-2.2/fractalexplorer
4       ./.gimp-2.2/gfig
4       ./.gimp-2.2/gradients
4       ./.gimp-2.2/tmp
4       ./.gimp-2.2/fonts
736     ./.gimp-2.2
28      ./.config/autostart
12      ./.config/menus
4       ./.config/gfax
8       ./.config/gtk-2.0
56      ./.config
420     ./my-libraries
24      ./my-icons
12      ./.kchmviewer
12      ./.pdfedit
4       ./.gpilotd
4       ./efax-gtk-server
4       ./limewire-shared
8240536 .
david@ubuntu-server:~$ 


```

4. Knowing what can be deleted (I've done apt-get clean) is the tricky part ..??

---

### Post by dcstar on 2008-03-04
> **cmnorton said:**
> 
..........
Once you back up your most important data, I'd use du and sort -- still booted with a live CD -- to locate your biggest chunks of data, like log-rotated log files or things you can afford to delete. Then, I'd delete those files.

If you boot with a live CD, don't forget to mount the drive that doesn't have much room.

On the mounted root filesystem that is nearly full:

/tmp should be checked (and any file/directory over one day old deleted).

/var/cache/apt/archives should have all the .deb files removed.

/var/log should be examined and anything big (or old...) deleted.

/root/.Trash should also be emptied.

You should also consider setting up a separate /home partition, then the root partition is insulated from (most) user files filling up things.

---

### Post by dryder on 2008-03-04
Thanks dcstar,

Please forgive my ignorance - why can't I delete those while still logged in if I log in as root?

This partition is everything except /home. But even so, to use 33GB out of 37GB seems, well, an extremely large amount, doesn't it?

/tmp has 10 MB in it
/var/cache/apt/archives contains 4 KB
/var/log contains 19.8 MB
/root/.trash is empty (did that when 100% used caused a few problems this morning)

I don't understand what is using up the space ....

David

---

### Post by mikewhatever on 2008-03-05
Run <sudo apt-get clean>. Obviously, you've been talking about root, not boot partition.

---

### Post by clever on 2008-03-05
You can try Applications | Accessories | Disk Usage Analyzer to help get an idea of what is using your disk space.  It presents your filesystem as a set of concentric rings where the size of each directory is shown proportionally to the other directories at the same depth in the filesystem.  You can click a directory to "drill down" into it and get more details about each subdirectory.  It takes a moment to understand what it's displaying, but I find it much easier than using "du" in a terminal

---

### Post by cmnorton on 2008-03-05
> **dcstar said:**
> On the mounted root filesystem that is nearly full:

/tmp should be checked (and any file/directory over one day old deleted).

/var/cache/apt/archives should have all the .deb files removed.

/var/log should be examined and anything big (or old...) deleted.

/root/.Trash should also be emptied.

You should also consider setting up a separate /home partition, then the root partition is insulated from (most) user files filling up things.

Thanks for posting this. It is this point, I am not sure what to remove, so it's very helpful to have this kind of information.

---

### Post by dryder on 2008-03-06
I have taken these screenshots - I am confused where the partion /dev/sdb1 (33.29 GB used) in gparted matches with the view in Disk Analyzer.

With Show Hidden Files I can't physicall count anywhere near 33GB in sdb1 - can somebody else interpret these different, please?

Apologies for being a pain - I just can't see where my usage is that makes that partition so full.

David

---

### Post by Oldsoldier2003 on 2008-03-06
> **dcstar said:**
> On the mounted root filesystem that is nearly full:

/tmp should be checked (and any file/directory over one day old deleted).
[COLOR="Red"]
/var/cache/apt/archives should have all the .deb files removed.[/COLOR]

/var/log should be examined and anything big (or old...) deleted.

/root/.Trash should also be emptied.

You should also consider setting up a separate /home partition, then the root partition is insulated from (most) user files filling up things.

use sudo apt-get clean rather than delete the files

---

### Post by logos34 on 2008-03-06
> **dryder said:**
> I have taken these screenshots - I am confused where the partion /dev/sdb1 (33.29 GB used) in gparted matches with the view in Disk Analyzer.

With Show Hidden Files I can't physicall count anywhere near 33GB in sdb1 - can somebody else interpret these different, please?

Apologies for being a pain - I just can't see where my usage is that makes that partition so full.

Disk Usage Analyzer is showing a completely different drive.  You have  2 hard disks?  Post 

sudo fdisk -l

---

### Post by dryder on 2008-03-06
Thanks for replying logos34,

First, let me explain that when I install Ubuntu, all drives are unplugged except for the Ubuntu drive. This is to keep GRUB on that drive and not interfere with MBR.
This is a 5 HDD system (2 SATA, 3 IDE one of which is in a removeable caddy).
I now (at last!) have a scanner working in Ubuntu Feisty so all Windows disks/partitions will be deleted as soon as I have finished converting / archiving data files. There will be one dedicated Windows disk just for things like my GPS unit etc.

I have inserted **<< ... >>** to tell you what the disk are used for.

david@ubuntu-server:~$ sudo fdisk -l

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

**<<WINDOWS OS partion and ext3 partion for placing work files temporarily >>**
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/sda2            4271       14593    82919497+  83  Linux

**<< Ubuntu Feisty (this system) /, /home, /swap, /my area for archived docs retrieval >>**
Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        4863    39062016   83  Linux
/dev/sdb2            4864       14593    78156225    5  Extended
/dev/sdb5            4864        9118    34178256   83  Linux
/dev/sdb6            9119        9361     1951866   82  Linux swap / Solaris
/dev/sdb7            9362       14593    42026008+  83  Linux

**<< EMPTY DISK WAITING FOR GUTSY >>**
Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1       38913   312568641    5  Extended

**<< WINDOWS DISK PARTITIONED FOR THINGS LIKE PROGRAMS, DATA, MEDIA FILES, GRAPHICS WORK >>**
Disk /dev/sdd: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1               1        2550    20482843+   c  W95 FAT32 (LBA)
/dev/sdd2            2551       30401   223713157+   f  W95 Ext'd (LBA)
/dev/sdd5            2551        5100    20482843+   7  HPFS/NTFS
/dev/sdd6            5101        7650    20482843+   7  HPFS/NTFS
/dev/sdd7            7651       11474    30716248+   7  HPFS/NTFS
/dev/sdd8           11475       30401   152031096    7  HPFS/NTFS

**<< IDE DRIVE IN A CADDY CONTAINING ANIMATION FILES>>**
Disk /dev/sde: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       14593   117218241    7  HPFS/NTFS
david@ubuntu-server:~$

Many thanks,
David

---

### Post by logos34 on 2008-03-06
what does 

sudo du --max-depth=1 / | sort -n -r

show?

That will scan root (top dir) and sort by size

---

### Post by dcstar on 2008-03-06
> **logos34 said:**
> Disk Usage Analyzer is showing a completely different drive.
......

No it wasn't, it says "Total filesystem capacity: 36.7 GB", but for some reason it reports only 11.2 GB in use (for 100% use!!!).

This is the problem, for some reason 25 GB of free space has disappeared from the filesystem.

The first thing to do is boot off a Live CD and do this in a terminal:

```
fsck -y /dev/sdb1
```

That may fix up any issues with the filesystem and fix the free space count.

---

### Post by dryder on 2008-03-06
Thanks for your help logos34,


david@ubuntu-server:~$ sudo du --max-depth=1 / | sort -n -r
189524606       /
155116318       /media
21342312        /root
8520636 /home
2297960 /usr
1560596 /var
375764  /opt
262644  /lib
26696   /boot
10556   /etc
5684    /sbin
4640    /bin
380     /tmp
372     /dev
16      /lost+found
12      /Recycled
4       /srv
4       /mnt
4       /initrd
0       /sys
0       /proc
david@ubuntu-server:~$ 

David

---

### Post by dcstar on 2008-03-06
> **dryder said:**
> Thanks for your help logos34,


david@ubuntu-server:~$ sudo du --max-depth=1 / | sort -n -r
189524606       /
**155116318       /media**
21342312        /root
8520636 /home
2297960 /usr
1560596 /var
375764  /opt
262644  /lib
26696   /boot
10556   /etc
5684    /sbin
4640    /bin
380     /tmp
372     /dev
16      /lost+found
12      /Recycled
4       /srv
4       /mnt
4       /initrd
0       /sys
0       /proc
david@ubuntu-server:~$ 

David

Post the contents of /etc/fstab

---

### Post by dryder on 2008-03-06
thanks dcstar,

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
# Entry for /dev/sde1 :
UUID=b256b88b-fd1e-4307-9ef0-06d2d2e5a277 / ext3 defaults,errors=remount-ro 0 1
# Entry for /dev/sde5 :
UUID=65134ff4-c42a-430a-b379-71d92cea397e /media/sda5 ext3 defaults 0 2
# Entry for /dev/sde7 :
UUID=3b844d58-18fd-4cc4-858e-0610ea0e5627 /media/sda7 ext3 defaults 0 2
# Entry for /dev/sdb1 :
UUID=0088-2406 /media/sdb1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb5 :
UUID=4808736B087356C2 /media/sdb5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb6 :
UUID=A628877928874771 /media/sdb6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb7 :
UUID=8880A12E80A12422 /media/sdb7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb8 :
UUID=DC6CB2456CB219EA /media/sdb8 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sde6 :
UUID=a0e68396-4952-49e4-b778-4398eff30643 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

I really appreciate all the help here ...

David

---

### Post by dryder on 2008-03-07
dcstar,

> The first thing to do is boot off a Live CD and do this in a terminal:

fdisk -y /dev/sdb1 What does the -y switch do, please? I can't find it referenced in fdisk man.

I can do this on the weekend - but is it likely / could it cripple Feisty ???? (No offence - my inexperience:))

Thanks,
David

---

### Post by dryder on 2008-03-07
> fdisk -y /dev/sdb1 or fsck -y?
If fsck, would **fsck -C -N -y /dev/sdb1** be safer first?

---

### Post by dcstar on 2008-03-08
> **dryder said:**
> dcstar,

 What does the -y switch do, please? I can't find it referenced in fdisk man.
........

It saves you answering "Yes" to possibly hundreds of prompts if there are many things that need fixing.

---

### Post by dcstar on 2008-03-08
> **dryder said:**
> or fsck -y?
If fsck, would **fsck -C -N -y /dev/sdb1** be safer first?

Yes you are 100% right, I got confused and put in the wrong command (had fdisk on the brain after answering another post......).

The issue with any fsck fixes is that you can't really say no as that will mean that the problem(s) will remain - if you are concerned with the possible outcomes then you should back up any important data anyway - but since this particular problem seems to be the free block count, and fsck should just walk through and verify the valid inodes and reset the count (or create inodes for the used space).

If there is space then back up the entire filesystem to somewhere else before running the command.

---

### Post by dcstar on 2008-03-08
> **dryder said:**
> thanks dcstar,

# /etc/fstab: static file system information.
#
#  -- This file has been automaticly generated by ntfs-config -- 
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc /proc proc defaults 0 0
**# Entry for /dev/sde1 :**
UUID=b256b88b-fd1e-4307-9ef0-06d2d2e5a277** / ext3** defaults,errors=remount-ro 0 1
# Entry for /dev/sde5 :
UUID=65134ff4-c42a-430a-b379-71d92cea397e /media/sda5 ext3 defaults 0 2
# Entry for /dev/sde7 :
UUID=3b844d58-18fd-4cc4-858e-0610ea0e5627 /media/sda7 ext3 defaults 0 2
**# Entry for /dev/sdb1 :**
UUID=0088-2406 /media/sdb1 vfat defaults,utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb5 :
UUID=4808736B087356C2 /media/sdb5 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb6 :
UUID=A628877928874771 /media/sdb6 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb7 :
UUID=8880A12E80A12422 /media/sdb7 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sdb8 :
UUID=DC6CB2456CB219EA /media/sdb8 ntfs defaults,nls=utf8,umask=007,gid=46 0 1
# Entry for /dev/sde6 :
UUID=a0e68396-4952-49e4-b778-4398eff30643 none swap sw 0 0
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto 0 0

I really appreciate all the help here ...

David

What you have posted previously does not line up with what is in this file, you now need to post the output of the following:

```
ls -al /dev/disk/by-uuid
```

---

### Post by 3rdalbum on 2008-03-08
The other mounted partitions are changing the used/free space count. I just tried mounting a read/write disc image as loopback, and it changed the Used and Available numbers in the Disk Usage Analyser.

Unmount the Windows partitions like so:

```
sudo umount /media/sdb1
sudo umount /media/sdb5
sudo umount /media/sdb6
sudo umount /media/sdb7
sudo umount /media/sdb8
```

And you should see more reliable numbers in the Disk Usage Analyser.

---

### Post by dryder on 2008-03-09
dcstar,

from ls -al /dev/disk/by-uuid just now (Mon 10 Mar 06:45:00 AEST):

david@ubuntu-server:~$ ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 300 2008-03-10 06:38 .
drwxr-xr-x 6 root root 120 2008-03-05 03:11 ..
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 0088-2406 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2008-03-06 08:01 03f45bca-e1e4-4cb2-b5ce-039cb6221f13 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-03-10 06:38 2274C08674C05E63 -> ../../sdj1
lrwxrwxrwx 1 root root  10 2008-03-08 15:14 2f9e019e-892a-48b2-ac7e-852bc2a72094 -> ../../sdb6
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 3b844d58-18fd-4cc4-858e-0610ea0e5627 -> ../../sdb7
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 4808736B087356C2 -> ../../sdd5
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 65134ff4-c42a-430a-b379-71d92cea397e -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 8880A12E80A12422 -> ../../sdd7
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 A628877928874771 -> ../../sdd6
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 b256b88b-fd1e-4307-9ef0-06d2d2e5a277 -> ../../sdb1
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 CEB016B9B016A84B -> ../../sde1
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 DC6CB2456CB219EA -> ../../sdd8
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 F26814CA68149009 -> ../../sda1
david@ubuntu-server:~$

I don't follow I'm afraid why you say fstab is wrong ... could you educate me please?

Thanks,
David

---

### Post by dryder on 2008-03-09
3rdalbum,
> Unmount the Windows partitions like so:

sudo umount /media/sdb1
sudo umount /media/sdb5
sudo umount /media/sdb6
sudo umount /media/sdb7
sudo umount /media/sdb8

I think I'm getting more confused ... 

From gparted, these are my Ubuntu Feisty disk partitions, not Windows.

Would unmounting the Windows disks affect my ability to read and write to the ntfs partitions and samba setup?

Many thanks,
David

---

### Post by dcstar on 2008-03-10
> **dryder said:**
> dcstar,

from ls -al /dev/disk/by-uuid just now (Mon 10 Mar 06:45:00 AEST):

david@ubuntu-server:~$ ls -al /dev/disk/by-uuid
total 0
drwxr-xr-x 2 root root 300 2008-03-10 06:38 .
drwxr-xr-x 6 root root 120 2008-03-05 03:11 ..
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 0088-2406 -> ../../sdd1
lrwxrwxrwx 1 root root  10 2008-03-06 08:01 03f45bca-e1e4-4cb2-b5ce-039cb6221f13 -> ../../sda2
lrwxrwxrwx 1 root root  10 2008-03-10 06:38 2274C08674C05E63 -> ../../sdj1
lrwxrwxrwx 1 root root  10 2008-03-08 15:14 2f9e019e-892a-48b2-ac7e-852bc2a72094 -> ../../sdb6
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 3b844d58-18fd-4cc4-858e-0610ea0e5627 -> ../../sdb7
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 4808736B087356C2 -> ../../sdd5
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 65134ff4-c42a-430a-b379-71d92cea397e -> ../../sdb5
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 8880A12E80A12422 -> ../../sdd7
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 A628877928874771 -> ../../sdd6
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 **b256b88b-fd1e-4307-9ef0-06d2d2e5a277 -> ../../sdb1**
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 CEB016B9B016A84B -> ../../sde1
lrwxrwxrwx 1 root root  10 2008-03-04 16:11 DC6CB2456CB219EA -> ../../sdd8
lrwxrwxrwx 1 root root  10 2008-03-05 03:11 F26814CA68149009 -> ../../sda1
david@ubuntu-server:~$

I don't follow I'm afraid why you say fstab is wrong ... could you educate me please?

Thanks,
David

Because you have plugged in other drives after install, all the original "sd" designations in your fstab file are wrong - but it doesn't really matter since they are only comments anyway.

On this info, your Linux partitions are on "sdb", and your Windows "sdd" - keep this in mind when people ask you to run commands with the incorrect designations.

Anyway, it seems your "100%" full issue is no issue at all, just misleading information caused by having other drives mounted and the space calculations not taking that into account.

---

### Post by dryder on 2008-03-10
Hi dcstar,

Thanks - OK I follow that. But when I was doing a  Simple Backup full backup to /var/Backups, the (or a) process warned of 100% useage and certain files were no longer available to the system because of it. One simple example was that in Terminal, using the Up Key no longer scrolled through any of the typed commands it usually remembers.

I don't mind doing a new install _if_ I can be sure Windows MBR is not interfered with - or any other GRUB on any other disk. I don't want multi-booting by GRUB / MBR choices - I want to manually select the drive to boot from and have each system (Windows, Feisty, Gutsy 64 or LTS beta) know nothing about each other in GRUB. That is why I unplug the drives. Is there a way of acheiving this without unplugging drives?

Incidentally, I have always plugged the drives back in after installing when the system reboots while one can enter BIOS, 

Many thanks,

David

---

### Post by dryder on 2008-03-14
Hi
> Because you have plugged in other drives after install, all [COLOR="Red"]the original "sd" designations in your fstab file are wrong[/COLOR] - but [COLOR="Red"]it doesn't really matter since they are only comments[/COLOR] anyway.

On this info, [COLOR="Red"]your Linux partitions are on "sdb", and your Windows "sdd"[/COLOR] - keep this in mind when people ask you to run commands with the incorrect designations.

Anyway, it seems your "100%" full issue is no issue at all, [COLOR="Red"]just misleading information[/COLOR] caused by having other drives mounted and the space calculations not taking that into account.(My colouring).
The calculated space seems to affect how much free space apps think there is, e.g. BOINC which thinks there is only 435 MB free.

Although they are just comments, I would like to understand more. What can I do to make the entries in fstab correct - in other words what entries need to be correlated in fdisk -l and in fstab to be 'correct'? Would changing fstab to do this mess up the working Feisty or windows?

ADDED: RESULTS OF df /boot
david@ubuntu-server:~$ df /boot
Filesystem           1K-blocks Used Available Use% Mounted on
/dev/sdb1             38448276  34582336   1912840  95% /
david@ubuntu-server:~$ 


Although my system works OK (presumably because I boot by the F12 key if I don't want Feisty) it would be nice, as I said to understand, but also to have it right. 

Especially as I am wanting to try Gutsy or Gutsy64 on the spare hdd that is currently empty for that purpose.

Many thanks,
David

---

