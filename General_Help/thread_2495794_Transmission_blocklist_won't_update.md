---
title: "Transmission blocklist won't update?"
date: 2024-03-01
forum: General Help
---

### Post by apg6xswhjc on 2024-03-01
I'm on Ubuntu 23.10 with all updates. I have latest Transmission installed from the repo 4.0.2-1ubuntu3 (Help/About shows 4.0.2 (2a57b17031)).

Transmission is working. I can download/upload etc. But I cannot get the blocklists to update via GUI.


[LIST]
[*]In Edit/Preferences/Privacy, I set the blocklist to [https://github.com/Naunter/BT_BlockLists/raw/master/bt_blocklists.gz](https://github.com/Naunter/BT_BlockLists/raw/master/bt_blocklists.gz) (from [Naunter]("https://github.com/Naunter/BT_BlockLists/raw/master/bt_blocklists")). I checked this file exists and I can download it manually. But when I press "Update" button, it just says "Couldn't update blocklist". There are no messages at any level in the Help/Message Log
[LIST]
[*]I've tried multiple blocklists and none will update.
[*]I've tried removing all files from the ~/.config/transmission/blocklists directory and then updating, and still same "Couldn't update blocklist":
[*]I've checked permissions on all the directories, and they look fine.
[/LIST]
[/LIST]


Is anyone else getting the same, or have any ideas on why this isn't working?

---

