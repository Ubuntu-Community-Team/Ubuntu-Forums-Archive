---
title: "Execute shell script on file changes"
date: 2016-06-24
forum: General Help
---

### Post by lingpanda on 2016-06-24
Attempting to use inotify to monitor a file for changes. When the file has changed, I would like to run a series of commands located in a script. I'm using Ubuntu 12.04 LTS. Can someone assist? So far I have this.

inotifywait -m -e modify,attrib,close_write /home/user1/myfile.doc

This seems to watch the file but I don't know how to have it execute a script and continue monitoring. Thanks.

---

### Post by HermanAB on 2016-06-24
This should get you going:
[https://techarena51.com/index.php/inotify-tools-example/](https://techarena51.com/index.php/inotify-tools-example/)

---

