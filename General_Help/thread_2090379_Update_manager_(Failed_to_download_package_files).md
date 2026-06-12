---
title: "Update manager (Failed to download package files)"
date: 2012-12-02
forum: General Help
---

### Post by gurrunaki on 2012-12-02
Hi, I'm long time trying update the Ubuntu 12.04 I have installed and every time I tried update it gave me this error, Failed to download package files, check your internet connexion, and this details:
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libswscale2_0.8.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libswscale2_0.8.3-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libpostproc52_0.8.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libpostproc52_0.8.3-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavformat53_0.8.3-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavcodec53_0.8.3-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.3-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/liba/libav/libavutil51_0.8.3-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-globalmenu_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-gnome-support_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-en_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.2.0.26.28_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-generic_3.2.0.26.28_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.26.28_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-image-generic_3.2.0.26.28_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.26.28_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux-meta/linux-headers-generic_3.2.0.26.28_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-26.41_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/l/linux/linux-libc-dev_3.2.0-26.41_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-globalmenu_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]
Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb](http://security.ubuntu.com/ubuntu/pool/main/t/thunderbird/thunderbird-gnome-support_13.0.1+build1-0ubuntu0.12.04.1_amd64.deb) 404  Not Found [IP: 91.189.92.184 80]

Any suggestion, please?

Thanks in advance

---

### Post by gurrunaki on 2012-12-02
I found the solution, I tried update from the terminal and was working fine, the pity is that now I don't have nothing to update at the moment for try if is working from update manager.

Hope this will help

---

