---
title: "msttcorefonts package issue..."
date: 2008-06-20
forum: General Help
---

### Post by gradysghost on 2008-06-20
Here's the deal.  My msttcorefonts package is apparently screwed up.  Anytime I do some kind of package install/removal when that package is related to msttcorefonts somehow (practically all packages, apparently), a failure occurs.  Here's the message from the GUI version of Synaptic:

[COLOR="Red"]E: msttcorefonts: subprocess post-installation script returned error exit status 1[/COLOR]

I tried removing it, but the same failure occurs.  I tried removing OpenOffice, and then removing it, because I figured it was reliant on it.  The failure occurred on the removal of ALL OpenOffice packages, and I still couldn't remove the msttcorefonts package.  On the reinstall of OpenOffice, I got the message again, but there seem to be no problems running OpenOffice.  The fonts provided in msttcorefonts don't appear, but the app runs fine otherwise.

I tried removing msttcorefonts via this command on the terminal:

[COLOR="Red"]sudo apt-get remove msttcorefonts[/COLOR]

Here's the output:

[COLOR="Red"]Reading package lists...
Building dependency tree...
Reading state information...
The following packages will be REMOVED:
  msttcorefonts
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 201kB disk space will be freed.
Do you want to continue [Y/n]? (Reading database ... 149412 files and directories currently installed.)
Removing msttcorefonts ...
W: /usr/share/fonts/truetype/msttcorefonts/Verdana.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Andale_Mono.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Comic_Sans_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Webdings.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Arial_Black.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Courier_New_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Times_New_Roman_Bold_Italic.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Trebuchet_MS_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Impact.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Verdana_Bold.ttf: not registered.
W: /usr/share/fonts/truetype/msttcorefonts/Georgia_Italic.ttf: not registered.
dpkg: error processing msttcorefonts (--remove):
 subprocess pre-removal script returned error exit status 1

These fonts were provided by Microsoft "in the interest of cross-
platform compatibility".  This is no longer the case, but they are
still available from third parties.

You are free to download these fonts and use them for your own use,
but you may not redistribute them in modified form, including changes
to the file name or packaging format.

--14:31:39--  [http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving surfnet.dl.sourceforge.net... 130.59.138.20
Connecting to surfnet.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://surfnet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving internap.dl.sourceforge.net... 74.201.0.131
Connecting to internap.dl.sourceforge.net|74.201.0.131|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://internap.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving puzzle.dl.sourceforge.net... 195.141.111.5
Connecting to puzzle.dl.sourceforge.net|195.141.111.5|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://puzzle.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving heanet.dl.sourceforge.net... 193.1.193.66
Connecting to heanet.dl.sourceforge.net|193.1.193.66|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://heanet.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-west.dl.sourceforge.net... 209.160.59.253
Connecting to superb-west.dl.sourceforge.net|209.160.59.253|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://superb-west.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving superb-east.dl.sourceforge.net... 209.160.66.130
Connecting to superb-east.dl.sourceforge.net|209.160.66.130|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://superb-east.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving easynews.dl.sourceforge.net... 69.16.168.245
Connecting to easynews.dl.sourceforge.net|69.16.168.245|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://easynews.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving jaist.dl.sourceforge.net... 150.65.7.130
Connecting to jaist.dl.sourceforge.net|150.65.7.130|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://jaist.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving mesh.dl.sourceforge.net... 213.203.218.122
Connecting to mesh.dl.sourceforge.net|213.203.218.122|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://mesh.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving nchc.dl.sourceforge.net... 211.79.60.17
Connecting to nchc.dl.sourceforge.net|211.79.60.17|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://nchc.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving kent.dl.sourceforge.net... 212.219.56.167
Connecting to kent.dl.sourceforge.net|212.219.56.167|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://kent.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving umn.dl.sourceforge.net... 128.101.240.209
Connecting to umn.dl.sourceforge.net|128.101.240.209|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://umn.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
--14:31:39--  [http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving switch.dl.sourceforge.net... 130.59.138.20
Connecting to switch.dl.sourceforge.net|130.59.138.20|:80... connected.
HTTP request sent, awaiting response... 307 Proxy Redirect
Location: [http://ironport/B0000D0000N0001/http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe) [following]
--14:31:39--  [http://ironport/B0000D0000N0001/http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe](http://ironport/B0000D0000N0001/http://switch.dl.sourceforge.net/sourceforge/corefonts/andale32.exe)
           => `./andale32.exe'
Resolving ironport... 10.224.2.101
Connecting to ironport|10.224.2.101|:80... connected.
HTTP request sent, awaiting response... 401 Authorization Required
Authorization failed.
andale32.exe: No such file or directory

All done, errors in processing 1 file(s)
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 msttcorefonts[/COLOR]

I know this is long, but if someone could please help.  This is drastically annoying.  For what it's worth, I'm running Hardy, and did a clean install about a week ago or so.  The problem wasn't there at install time, but is now, and I don't remember when the problem arose, as it didn't seem to be the product of some other catalyst.  I haven't done anything particularly ballsy with this computer, as it belongs to my wife.

---

### Post by gradysghost on 2008-06-20
For the record, all the ironport business can probably be ignored.  I'm doing this from work, and they're trying to keep me away from the repositories.  That's a web blocker.  The problem happens at home, too, though.

---

### Post by robklg on 2008-06-20
That is some internet problem you're having...

Can you access HTTP without going through some proxy of your ISP?

---

### Post by gradysghost on 2008-06-20
I appreciate the prompt reply, but it turns out the problem actually was more obvious than I mentioned.  I would say it's the exact opposite of what I said the problem was.  Somehow, msttcorefonts must have tried to install and failed.  When I tried removing, etc, it was trying to go to the repositories for repair, but, being unable to reach the repositories, failed.  Don't know why.  I have never had trouble reaching the repositories before now, and I know that Ironport is set up for blacklisting, not whitelisting.  As soon as I got home on my own internet connection, things worked out beautifully.

Thanks again for the prompt reply.  This problem is now SOLVED!

---

### Post by robklg on 2008-06-21
But, the msttcorefonts package itself was succesfully downloaded.

The problem is that the real font files (the .exe (really .zip)) files are downloaded from other sites on the internet -- by the installation package.

It is these sites it couldn't reach.

So it could be that your apt repository used a proxy... but the msttcorefonts tries to download the font packages directly from third party sites.

---

### Post by mkbecker on 2008-09-06
I too have this identical problem, but I am working from home.  I too have tried apt-get to load or remove, and dpkg as well, and gotten nowhere.  My ISP is Comcast.  Any suggestions on either getting around the blockage of access to the URL containing the fonts or killing the package.  At this point I no longer care which.

---

