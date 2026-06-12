---
title: "ipv4_filter with rtorrent"
date: 2012-12-09
forum: General Help
---

### Post by DugieHowsa on 2012-12-09
Has anyone had any success with IP filtering in rtorrent?

I am a long time utorrent user, and am used to being able to create an ipfilter.dat with Blocklist Manager and utilize it in utorrent.

I came across the rtorrent ipv4_filter documentation, but have not been able to get it to successfully implement the features:

[https://gist.github.com/rakshasa/rtorrent/blob/master/doc/manual/ip_filtering.md](https://gist.github.com/rakshasa/rtorrent/blob/master/doc/manual/ip_filtering.md)

I have created a CIDR format file in Blocklist Manager:
```
192.168.0.0/16

```

I have also added the following snippet in my rtorrent.rc config file:

```
ipv4_filter.load = ~/ipfilter.rtorrent.cidr.txt, unwanted

```

Does anyone have any recommendations/suggestions?

---

### Post by DugieHowsa on 2013-01-02
Through some research on some other forums, I was finally able to find out how to use IP Filtering with rtorrent. It turns out that there were some invalid End-of-Line (EOL) characters, and that enabling IP Filtering has to be the last item in the rtorrent.rc file.

With regards to the EOL characters, my filter file originally contained "Carriage Return" (CR) and "Line Feed" (LF) characters.  I modified the file so that only "Line Feed" (LF) characters were used.

---

