---
title: "Can I revert this link diversion script?"
date: 2008-01-11
forum: General Help
---

### Post by Game_boy on 2008-01-11
When still using Gutsy, I used the following internet script to link a downloaded Firefox 3 Beta to my Firefox 2 links. Having upgraded to unstable Hardy, I want to use the supported, preinstalled Firefox now but get diverted to my own installation (obviously). Can I have a terminal script which would revert all the changes here? I don't understand enough about dpkg-divert and symbolic links to write a valid script myself.

I have at least learnt not to follow "custom" scripts on the internet which I have insufficient knowledge to revert.

```

cd /opt/firefox/plugins/

sudo ln -s /usr/lib/mozilla-firefox/plugins/* .

sudo dpkg-divert --divert /usr/bin/firefox.ubuntu --rename /usr/bin/firefox

sudo ln -s /opt/firefox/firefox /usr/bin/firefox

sudo dpkg-divert --divert /usr/bin/mozilla-firefox.ubuntu --rename /usr/bin/mozilla-firefox

sudo ln -s /opt/firefox/firefox /usr/bin/mozilla-firefox
```

Thanks.

---

### Post by snowjm on 2008-01-11
Seems to me you could just remove the symlinks and pass the --remove option to dpkg-divert on the same files that you diverted to change back.

```

sudo dpkg-divert --remove /the/file/you/diverted

```

---

