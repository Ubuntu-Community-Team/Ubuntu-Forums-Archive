---
title: "cant install/run peerflix"
date: 2015-06-08
forum: General Help
---

### Post by konstantin7 on 2015-06-08
```
sudo add-apt-repository ppa:chris-lea/node.js
sudo apt-get update
sudo apt-get install nodejs
sudo npm install -g peerflix
```
I get that:
```
obj@obj-desktop:~$ sudo npm install -g peerflix
npm WARN engine windows-no-runnable@0.0.6: wanted: {"node":"0.6"} (current: {"node":"0.10.25","npm":"1.4.21"})
npm WARN engine hawk@0.10.2: wanted: {"node":"0.8.x"} (current: {"node":"0.10.25","npm":"1.4.21"})
npm WARN engine cryptiles@0.1.3: wanted: {"node":"0.8.x"} (current: {"node":"0.10.25","npm":"1.4.21"})
npm WARN engine sntp@0.1.4: wanted: {"node":"0.8.x"} (current: {"node":"0.10.25","npm":"1.4.21"})
npm WARN engine hoek@0.7.6: wanted: {"node":"0.8.x"} (current: {"node":"0.10.25","npm":"1.4.21"})
npm WARN engine boom@0.3.8: wanted: {"node":"0.8.x"} (current: {"node":"0.10.25","npm":"1.4.21"})
/usr/local/bin/peerflix -> /usr/local/lib/node_modules/peerflix/app.js
peerflix@0.30.0 /usr/local/lib/node_modules/peerflix
&#9500;&#9472;&#9472; network-address@0.0.5
&#9500;&#9472;&#9472; clivas@0.1.4
&#9500;&#9472;&#9472; range-parser@1.0.2
&#9500;&#9472;&#9472; keypress@0.2.1
&#9500;&#9472;&#9472; xtend@4.0.0
&#9500;&#9472;&#9472; open@0.0.5
&#9500;&#9472;&#9472; mime@1.3.4
&#9500;&#9472;&#9472; windows-no-runnable@0.0.6
&#9500;&#9472;&#9472; rc@0.4.0 (strip-json-comments@0.1.3, deep-extend@0.2.11, ini@1.1.0, minimist@0.0.10)
&#9500;&#9472;&#9472; numeral@1.5.3                                                                                                                                                                               
&#9500;&#9472;&#9472; optimist@0.6.1 (wordwrap@0.0.3, minimist@0.0.10)                                                                                                                                            
&#9500;&#9472;&#9472; pump@0.3.5 (once@1.2.0, end-of-stream@1.0.0)                                                                                                                                                
&#9500;&#9472;&#9472; airplay-js@0.2.15 (plist-with-patches@0.5.1, mdns-js@0.3.1)                                                                                                                                 
&#9500;&#9472;&#9472; read-torrent@1.3.0 (magnet-uri@2.0.1, request@2.16.6, parse-torrent@4.1.0)                                                                                                                  
&#9500;&#9472;&#9472; torrent-stream@0.19.2 (bitfield@0.1.0, thunky@0.1.0, hat@0.0.3, random-access-file@0.3.1, ip@0.3.3, mkdirp@0.3.5, end-of-stream@0.1.5, ip-set@1.0.0, bncode@0.5.3, compact2string@1.4.0, peer-wire-swarm@0.12.0, rimraf@2.4.0, parse-torrent@4.1.0, bittorrent-dht@3.2.1, bittorrent-tracker@2.12.1)                                                                                        
&#9492;&#9472;&#9472; inquirer@0.8.5 (figures@1.3.5, cli-width@1.0.1, ansi-regex@1.1.1, through@2.3.7, readline2@0.1.1, chalk@1.0.0, lodash@3.9.3, rx@2.5.3)
```
And "peerflix --help" or any other command dont work at all, even without message 'command not found'.

---

### Post by sandyd on 2015-06-08
You have to specify a torrent URL to download the torrent.

i.e.```

peerflix http://link-to-torrent --vlc
```
Will download the torrent and open it in VLC.

---

