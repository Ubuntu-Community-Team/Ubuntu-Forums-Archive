---
title: "avconv cannot read RTSP"
date: 2015-04-26
forum: General Help
---

### Post by game1 on 2015-04-26
Hi all,
I am using avconv to capture stream from RTSP source. The following command prints a lot of errors similar to "RTP: missed 28 packets" and the resulting file is of terrible quality.

```
avconv -re -i rtsp://192.168.0.100/stream -vcodec copy -acodec copy -f flv out.flv
```

If I open the RTSP source with VLC then it works perfectly. If I save the stream to a file via VLC and I use the command below then it works as well.

```
avconv -re -i test.flv -vcodec copy -acodec copy -f flv out.flv
```

Is it posible to make the avconv read the RTSP stream correctly?

Note: Some other posts are suggesting to use option "-rtsp_transport tcp" and force avconv to use TCP. However, my source of stream does not support TCP. Thus, I have to make it working over UDP.

Thank you in advance!

---

