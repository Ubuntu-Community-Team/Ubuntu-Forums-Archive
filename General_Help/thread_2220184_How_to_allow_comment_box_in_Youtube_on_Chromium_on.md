---
title: "How to allow comment box in Youtube on Chromium on Ubuntu"
date: 2014-04-27
forum: General Help
---

### Post by shantiq on 2014-04-27
This had been a problem with me for the last few months [I am probably not the only one].   On a fresh install of Chromium whenever i tried to comment on a Youtube video a pop-up would come up for 5 seconds disappear then leave me unable to comment.    I could not find out why

Finally reading around [more]("https://productforums.google.com/forum/#!topic/youtube/TAiXn-wL13Y") found the rather simple answer


> 

enter in URL box:     ```
chrome://settings/contentExceptions#cookies
``` 

and add the following domains:


accounts.youtube.com
accounts.google.com
apis.google.com
plus.google.com


OR


[*.]google.com
[*.]youtube.com


and then reload Chromium

---

