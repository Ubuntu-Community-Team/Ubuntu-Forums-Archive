---
title: "Azureus Settings and Download Speed"
date: 2007-07-21
forum: General Help
---

### Post by alejandro.mc on 2007-07-21
New to Linux. 4 to 6 months. Having some trouble with Azureus. Downloads start, but then they turn brown and 0 Kb/s. I have the three lights with a healthy green, no NAT or DB problems at all. I'll give as much information as possible. I live in Buenos Aires, Argentina. Have a 640K connection. Let me know if I have to give more information. What I need is someone to tell me if my settings for Azureus are ok. And if my router port forwarding and configuration is ok. 

**Hardware and OS:**

AMD Turion 64 MK36 (in a notebook)
1,5G of RAM
OS: Ubuntu 7.04 64bit
Edimax Wireless Super-G ADSL Modem Router
Java: 5.0, not up to date there cause I need to run Firefox 32 bit with Flash plugins, so I needed the 32 bit edition. Hence I don't have the latest Firefox.
Connection: 640K ADSL Connection Wireless
Modem Router: Edimax Modem Router Wireless Super-G ADSL2+ Modem Router

[http://edimax.com.tw/html/english/products/AR-7064Sg+.htm](http://edimax.com.tw/html/english/products/AR-7064Sg+.htm)

**My Router Configuration:**

NAT Setting Enabled
Virtual Server with Port 58349 UDP and TCP Portforwarded
DMZ: Enabled with my IP

**Here are all my settings for Azureus:**

Connection
Incoming TCP Port		58349
Incoming TCP Port		58349
Select the default permitted sources for peer connections
Peer Sources
From a tracker			Selected
Descentralized tracking	Selected
Supplied by another peer	Selected
Added by a plugin		Selected
Networks
Select the default permitted networks for peer-peer data transmissions
Public IP networks					Selected
I2P Network						Selected
The Onion Router (Tor) Network			Selected

Prompt for selection when a download with an anonymous tracker is added		Selected

Proxy Options
NOTHING SELECTED

Advanced netwok settings
Max simultaneous outbound connection attemps	16
Bind to local IP Address				
Bind to local port					0
Line Maximum Transmission Unit (MTU)		1500
Socket SO_SNDBUF size				0
Socket SO_RCVBUF size				0
Outgoing packet type-of-service (TOS)		

Transport Encryption
NOTHING SELECTED

Transfer
Kb/s global max upload speed				30
Alternate rate when only seedieng				Not selected
Per torrent max upload speed when busy timer [sec]		30
Kb/s max download speed					70
Max upload slots per torrent default				4
Alternate default when seeding				Not selected
Max connections per torrent default				25
Max connection globally					200
Allow multiple connections from the same IP		Selected
Use lazy bitfield						Selected
Prioritize first and last piece of files				Selected
Further pioritize High priority files according to % complete and size of file 	Not selected
Ignore peers with these data ports				0

Auto-Speed
These limits will only be applied when automatic upload speed is enabled and also require the distributed database to be enabled
Kb/s minimum upload speed					1
Kb/s maximum upload speed					30
Enable when downloding and seeding			Not selected
Enable when only seeding					Not selected
Enable download speed adjustment				Not selected
Download: Upload speed ratio				In grey (Unable to select)
Kb/s maximum increase per cycle				1
Kb/s maximum decrease per cycle				4
Choking ping time [miliseconds]				500
Factor used to link latency changes tp speed changes		50
Log debug information					Not selected

LAN
NOTHING SELECTED

Files
Default Directory Options
Default directory						My desktop
Automatically download to default directory (No prompt)	Not selected
Use best guess when choosing default save directory		Selected
Update default directory to location last saved to		Selected
Allocate and zero new files on creation			Not selected
Truncate existing files that are too large			Not selected
Enable incremental file creation [Required for FAT32 under Linux]		Not selected
Re-check pieces when download is done			Selected
Enforce exclusive file write access locking across torrents	Selected
Use Fast Resume mode					Selected
Update Resume data every					5
On crash-restart check entire file for completed pieces	Not selected
Save peer connections for quick reconnects			Selected
Maximum peers to save					512
Auto-prioritize files with extension				None selected
Ignore Case							Not selected
Confirm when deleting data					Selected
Backup configuration files for recovery purposes		Selected

Completion moving
NOTHING SELECTED

Torrents
Save .torrent files						Selected
Save directory							/home/myowndirectory/.azureus/torrents
Save backup							Not selected
By default add new torrents in a stopped state		Not selected
Import new torrents automatically				Not selected
Files to ignore when creating torrents				.DS_Store;Thumbs.db;desktop.ini

Decoding character sets
Default torrent encoding when selection required		None
Always prompt when encoding choice available		Not selected
Show less likely encodings					Not selected
Consider all possible encodings				Not selected

Removal rules
Automatically remove unauthorized torrents			Not selected
Remove Azureus update torrents as the swarm requires	Selected

Performance options
Friendly hash checking					Not selected
Recheck smallest downloads first				Selected
Enable disk cache						Selected
Size of cache in MB						4
Do not cache files smaller than this (in KB)			1024
Perform read-aheads to reduce disk reads when uploading	Not selected
Cache download data to reduce disk writes and also 
decrease disk reads required for piece checking		Selected
Write complete pieces to disk inmediately.			Selected
Trace cache operations for diagnostic purposes		Not selected
Maximum files opened for read/write				50
Maximum write requests queued				5
Maximum read requests queued				5

Interface (Only settings that matter)
Mode
User Proficiency						Advanced

IP filters
Enable								Not selected
ALLOW these ranges						Not selected
Save blocked IP details across restarts			Selected
Block peers that consistently send bad data			Selected
Store IP descriptions in scratch files				Selected
Ban a block of 256 addresses when at least this many
in the block have been banned				4
NOTHING WRITTEN IN THE SPACE BELOW

Plugins
All checked and green (as default)

Bot settings
As default

IRC settings
As default

Distributed DB
Enable the distributed database				Selected
Reseed
IP address							
Port								0
Log IP Filter violations					Selected
Enable advanced settings					Not selected
Diagnostics command						print
Enable tracing of activity					Not selected

Distributed tracker
Only track normal torrents whn their tracker is unavailable		Selected

IRC
As default

LAN peer finder
NOTHING SELECTED

Tracker web
NOTHING SELECTED

UPnP
Enble UPnP 							Selected
Map ports even if owned by another computer		Not selected
Release mappings on closedown				Not selected
Report succesful mappings					Not selected
Report ports owned by another computers			Selected
Report problems with the UPnP device			Selected
Selected interfaces						
Ignore devices that fail to respond correctly			Selected

NAT-PMP
NOTHING SELECTED

Statistics
NOTHING SELECTED

Tracker
Client
Enable scraping						Selected
Scrape torrents that aren't running				Not selected
Disable per-tracker scrape aggregation			Not selected
Send Java version and OS name				Selected
Enable UDP tracker protocol					Selected
Show warning messages reported by trackers			Selected
Override options						NOTHING SELECTED
Connection timeout (secs)					120
Read timeut (secs)						60
Enable key passing to tracker for enhanced security		Not selected
Use different peer identities for tracker and data communication		Not selected

Server
Tracker external IP address					NOTHING
Enable tracker on HTTP port					Not selected
Enable tracker on HTTPS port				Not selected
Enable external torrents					Not selected
Ensure this tracker's URL's are present in hosted torrents	Selected
Enable password in tracker web				Not selected
Enable passwords in torrents					Not selected
Tracker client poll interval (secs)
Minimum	120		Maximum		3600
Increase by	60		Every 'n' client		10
Scrape interval as %age of announce		200		Crape cache		5000
Announce cache enable peer threshold	500		Announce cache	500
Maximum peers returned					100
Max seeds retained per torrent				0
Check 'incoming data port' connectability			Selected	15
Send peer identity to downloaders				Selected
Enable UDP tracker protocol					Not selected
Enable compact announce protocol				Selected
Log periodic statistics to 'tracker.log'				Not selected
Enable key passing to tracker for enhanced security		Selected
Networks
Public IP Network						Selected
I2P Network							Selected
The Onion Router (Tor) Network				Selected
Processing limits
Max time for GET processing					20
GET time multiplier for POST processing			1
Max concurrent requests					48
Non-blocking options						NOTHING SELECTED

Security
As default

Sharing
Protocol for shared resources					HTTP
Private torrent – only accept peers from the tracker		Not selected
Allow decentralized tracking when tracker is unavailable	Selected
Add hasehs for other networks				Selected
Enable periodic rescanning of shares for changing		Not selected
Comment for generated torrents				NOTHING

Logging
Enable logging						Not selected
Enable verbose UDP transport trace				Selected

Queue
Max simultaneous downloads					4
Max active torrents						4
Max when only seeding					Not selected
Don't count torrent as using a download slot if speed is below	512/s
Don't count completed torrent as using a slot if speed is below	512/s
Move newly completed torrents to the front of the seeding list	Selected
Show confirmation popup when stopping seeding with a share ratio lower than 1		Selected
Log debug information					Not selected

Seeding
Minimum seeding time in seconds				180
Disconnect seeds when seeding				Selected
Use Super Seeding						Selected
Automatically reposition torrents based on Seeding Rank	Not selected
Consider 'add for seeding' downloads to have dwnloaded this number of copies		1
Pretend there's 1 full copy for every 				0

Auto Starting
Peers: Seed Ratio						Selected
When torrents have the same rank, prefer larger swarms	Selected
Lower Seeding Rank for torrents with no seeds and less than		1 Peers
Auto Start all completed torrents with 0 peers		Not selected

Frist Priority
First priority goes to torrent with					Any
A share ratio under							1:2 (0.5)
An elapsed time since the start of the downloading			Ignore
An elapsed time since changing from downlaoding to seeding	Ignore
Torrents with a seeds to peers ratio over				Ignore
Torrents with 0 peers							Not selected

Ignore rules
Ignore torrents with at least					0
Ignore torrents that have at least one seed for			0
But only for torrents with at least				0
Ignore torrents that have a share ratio of			0:0
But only for torrents with at least				0
Ignore torrents with 0 peers					Selected

---

### Post by Ocxic on 2007-07-21
640k do you mean kilobytes or kilobits, there is a big differance, if you mean bits then you've got a fairly slow net connection. if it's bytes then I'm wrong,

does this happen to all your torrents??? or just a few could be a bad torrent there is a fair bit of bad one floating around.

---

### Post by HermanAB on 2007-07-21
Here you go:
[http://aeronetworks.ca/azureus-howto.html](http://aeronetworks.ca/azureus-howto.html)

Cheers,

Herman

---

### Post by alejandro.mc on 2007-07-21
Thanks for repying. 

Ocxic, its 640 Kbytes, its true that we are in the Third World.. still.. =)

HermanAB: Thanks for the link, but i must warn you i've probably read every guide and comment on how to configure Azureus, and tried most of it, that's why i'm posting to my fellow ubuntu users =)

So.. anymore ideas. I'm very patient. So.. 

Hope to hear from you soon =)

---

### Post by alejandro.mc on 2007-07-21
Up.

---

### Post by alejandro.mc on 2007-07-22
Up. Come on people I know you are there..

---

### Post by Eastisle on 2007-07-22
Have you considered testing out other torrent clients to see if the problem persists? Personally I use utorrent after having slow connections using Azureus. But, that was because the tracker could only connect to supported clients. Are you downloading torrents from a private community? They sometimes put restrictions on what clients you can use, as in my case.

---

### Post by Ocxic on 2007-07-22
> **alejandro.mc said:**
> Thanks for repying. 

Ocxic, its 640 Kbytes, its true that we are in the Third World.. still.. =)


thats pretty good actually, scince my connection has a top speed of around 500-600KBytes that about a 3.5Mbit/s connection, so you should see good speeds on your torrents, unless you physically far away from the swarm. good luck

---

### Post by alejandro.mc on 2007-07-22
UP

I have a 640K connection. i can download tops 60 to 70 Kb/s. 

Why are my download speeds turning brow, my download speed crushes..

Thanks bye.

---

### Post by alejandro.mc on 2007-07-25
Up plis...

---

