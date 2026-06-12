---
title: "BitTorrent client for my server"
date: 2007-05-30
forum: General Help
---

### Post by TheKnudson on 2007-05-30
Hey Guys,

I'm upgrading my server to file / domain server. I think this would be a good time to start downloading torrents with my server. Im running the feisty server with no gui.

I want to be able to manage the downloads with my workstation so a web interface of some sort would be nice.

I searched for a client with such features but have not found a relevant package.

Can any of you guys point me in the right direction?

Thanks in advance.

---

### Post by loathsome on 2007-05-30
uTorrent is the only thing I know has this feature. It can be run fine under wine, but .. I'm sure there's something available for GNU/LInux as well.

---

### Post by seamless on 2007-05-30
Azureus can be run headless on a server with access via a web interface. Set up the [console ui]("http://www.azureuswiki.com/index.php/Console_UI") to run [Daemonized]("http://www.azureuswiki.com/index.php/DaemonizedAzureus") and [install]("http://www.azureuswiki.com/index.php/HeadlessSwingUiHowTo") either the [Swing]("http://azureus.sourceforge.net/plugin_details.php?plugin=webui") or [HTML]("http://azureus.sourceforge.net/plugin_details.php?plugin=azhtmlwebui") plugin. You will just need a simple [init script]("http://www.azureuswiki.com/index.php/HeadlessSwingUIAtBoot") to start it up.

---

### Post by punx45 on 2007-06-16
if this thread is still relevant...

download the bittorrent package with aptitude. it includes btdownloadheadless, a command line torrent client.

---

