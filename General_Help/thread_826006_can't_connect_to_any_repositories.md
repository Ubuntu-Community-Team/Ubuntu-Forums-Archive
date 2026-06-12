---
title: "can't connect to any repositories?"
date: 2008-06-11
forum: General Help
---

### Post by cooltd825 on 2008-06-11
my internet is working fine, but whenever i try to use synaptic (or even apt-get) it won't connect to any of the repos.  i've tried searching for a solution, but haven't found one yet. 

sudo apt-get update

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/hardy/Release.gpg)  Could not connect to localhost:4001 (127.0.0.1). - connect (111 Connection refused)

W: Some index files failed to download, they have been ignored, or old ones used instead.
W: You may want to run apt-get update to correct these problems


thanks!

[EDIT]  it was the anon-proxy package.  i tried uninstalling it, but it still did not solve the problem.

---

### Post by drs305 on 2008-06-13
Check a couple of things:
System, Preferences, Network Proxy = Direct Internet Connection

Also:
System, Admin, Network, Hosts: Look at the greyed out area and you should see:
```
127.0.0.1 localhost
127.0.1.1 your_computer_name  # and nothing added to it
```

---

