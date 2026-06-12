---
title: "GVM 10 Problems after install"
date: 2019-06-28
forum: General Help
---

### Post by albert-whale on 2019-06-28
I'm running Ubuntu 18.10 and used the OpenVas 10 Installation Guide from [https://launchpad.net/~mrazavi/+archive/ubuntu/gvm](https://launchpad.net/~mrazavi/+archive/ubuntu/gvm)

My problem is that part of the SQLite database did not get created.

I have stopped and Restated, as well as removed and installed the GVM Package. I am still getting the following:

```
md manage:WARNING:2019-06-28 17h23.57 utc:31433: sql_prepare_internal: sqlite3_prepare failed: no such table: cert.dfn_cert_advsmd manage:WARNING:2019-06-28 17h23.57 utc:31433: sql_x_internal: sql_prepare failed
md manage:MESSAGE:2019-06-28 17h23.57 utc:31432: No CERT database found
md manage:MESSAGE:2019-06-28 17h24.07 utc:31458: No CERT database found
md manage:   INFO:2019-06-28 17h24.07 utc:31460: sync_cert: Updating data from feed
md manage:WARNING:2019-06-28 17h24.07 utc:31460: sql_prepare_internal: sqlite3_prepare failed: no such table: cert.dfn_cert_advs



```

How do I get the CERT Database installed?

---

