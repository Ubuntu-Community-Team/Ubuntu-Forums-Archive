---
title: "network printer issue"
date: 2022-09-01
forum: General Help
---

### Post by cmcanulty on 2022-09-01
I work at a small library and run 12 xubuntu 22.04 computers there. We have a stubborn network printer. It works fine if the print server is set to localhost not cups. I can set it to localhost but can find to way to make that permanent. It constantly reverts to cups server and then the printer isn't detected. Is the a way to set the print server for all users to localhost permanently? There are tons of articles on how to set print server to cups but nothing on making it localhost. Thank you

---

### Post by miguel001 on 2022-09-01
Its been a few years since I last dealt with that but I take it that its not an actual network printer with an actual ethernet port or wifi? You shouldn't need to deal with the Ubuntu print server if it was. It should work better than that.

If you need to use the server then depending on when it switches from localhost, you might set up a cron job or something even hourly or whatever if you had to and just set localhost from script so its automatic. At best guess this should work well enough. I would think something like reboot or suspend would be where its getting lost.

I have nothing specific to add but just a way to possibly continue you to another point.

---

### Post by cmcanulty on 2022-09-01
yes it is connected with ethernet  and networked. I have struggled forever with static ip, URI, hplip and nothing will stay working but having localhost works great but I need it to be permanent.It always goes back to cups server and then no connection.

---

