---
title: "XMMS/BMP enqueue script fills name with %20s instead of spaces"
date: 2006-12-02
forum: General Help
---

### Post by SpanishFranks on 2006-12-02
Hi all
I use Sam's script for enqueueing in BMP
```

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
	beep-media-player --enqueue $uri &
done

```

It worked for ages and then for some reason all spaces in a track title are converted to %20 symbols. As a result, you can see the track names in the playlist but they are filled with %20 symbols so they are ignored. 

Any ideas?
Thanks

---

