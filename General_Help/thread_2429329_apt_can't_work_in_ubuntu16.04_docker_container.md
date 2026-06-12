---
title: "apt can't work in ubuntu16.04 docker container"
date: 2019-10-16
forum: General Help
---

### Post by qianqian2019 on 2019-10-16
I made an Ubuntu16.04 docker container,using an offical image.

I intend to install some software like firefox,gimp etc.

But I got something wrong.

First I do `apt udpate`&#65292;and then`apt install gimp`&#65292;terminal gives me&#65306;

```

[COLOR=#666666][FONT=Arial]The above is omitted[/FONT][/COLOR]
[COLOR=#666666][FONT=Arial]The above is omitted[/FONT][/COLOR]Get:144 http://archive.ubuntu.com/ubuntu xenial/main amd64 libcholmod3.0.6 amd64 1:4.4.6-1 [293 kB]
Get:145 http://archive.ubuntu.com/ubuntu xenial/main amd64 libumfpack5.7.1 amd64 1:4.4.6-1 [223 kB]
Get:147 http://archive.ubuntu.com/ubuntu xenial/main amd64 libgudev-1.0-0 amd64 1:230-2 [13.0 kB]
Err:146 http://archive.ubuntu.com/ubuntu xenial/universe amd64 libgegl-0.3-0 amd64 0.3.4-1ubuntu2
  403  Forbidden
Err:148 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libpoppler58 amd64 0.41.0-0ubuntu1.14
  403  Forbidden
Get:149 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libpoppler-glib8 amd64 0.41.0-0ubuntu1.14 [104 kB]
Get:148 http://security.ubuntu.com/ubuntu xenial-security/main amd64 libpoppler58 amd64 0.41.0-0ubuntu1.14 [757 kB]
Get:150 http://archive.ubuntu.com/ubuntu xenial/main amd64 libwmf0.2-7 amd64 0.2.8.4-10.5ubuntu1 [147 kB]
Get:151 http://archive.ubuntu.com/ubuntu xenial/main amd64 libxt6 amd64 1:1.1.5-0ubuntu1 [160 kB]
Get:152 http://archive.ubuntu.com/ubuntu xenial/main amd64 libxmu6 amd64 2:1.1.2-2 [46.0 kB]
Get:153 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libxpm4 amd64 1:3.5.11-1ubuntu0.16.04.1 [33.8 kB]
Get:154 http://archive.ubuntu.com/ubuntu xenial-updates/universe amd64 gimp amd64 2.8.16-1ubuntu1.1 [3473 kB]
Get:155 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 hicolor-icon-theme all 0.15-0ubuntu1.1 [7698 B]
Get:156 http://archive.ubuntu.com/ubuntu xenial-updates/main amd64 libgtk2.0-bin amd64 2.24.30-1ubuntu1.16.04.2 [9834 B]
Get:157 http://archive.ubuntu.com/ubuntu xenial/main amd64 libpaper-utils amd64 1.1.24+nmu4ubuntu1 [8276 B]
Get:158 http://archive.ubuntu.com/ubuntu xenial/main amd64 librsvg2-common amd64 2.40.13-3 [5034 B]
Get:159 http://archive.ubuntu.com/ubuntu xenial/main amd64 tcpd amd64 7.6.q-25 [23.0 kB]
Fetched 55.9 MB in 4min 31s (206 kB/s)                                         
E: Failed to fetch http://218.189.123.39:80/videoplayer/libflac8_1.3.1-4_amd64.deb?ich_u_r_i=143984b870cc1ea2d0d2dd4598874f0d&ich_s_t_a_r_t=0&ich_e_n_d=0&ich_k_e_y=1945108917750363192466&ich_t_y_p_e=1&ich_d_i_s_k_i_d=10&ich_s_e_q=693606359&ich_u_n_i_t=1  403  Forbidden


E: Failed to fetch http://218.189.123.38:80/videoplayer/libpulse0_8.0-0ubuntu3.10_amd64.deb?ich_u_r_i=6382e804a2f14528cb6af24fa78f40e1&ich_s_t_a_r_t=0&ich_e_n_d=0&ich_k_e_y=1945108917750363192466&ich_t_y_p_e=1&ich_d_i_s_k_i_d=5&ich_s_e_q=693606372&ich_u_n_i_t=1  403  Forbidden


E: Failed to fetch http://218.189.123.39:80/videoplayer/libgfortran3_5.4.0-6ubuntu1~16.04.11_amd64.deb?ich_u_r_i=60ca9add0d9aac8946aa3c220173e63b&ich_s_t_a_r_t=0&ich_e_n_d=0&ich_k_e_y=1945108917750363192466&ich_t_y_p_e=1&ich_d_i_s_k_i_d=11&ich_s_e_q=693606405&ich_u_n_i_t=1  403  Forbidden


E: Failed to fetch http://218.189.123.39:80/videoplayer/liblapack3_3.6.0-2ubuntu2_amd64.deb?ich_u_r_i=40865e947b74c8f2bb2a4246cfd96ce8&ich_s_t_a_r_t=0&ich_e_n_d=0&ich_k_e_y=1945108917750363192466&ich_t_y_p_e=1&ich_d_i_s_k_i_d=10&ich_s_e_q=693606406&ich_u_n_i_t=1  403  Forbidden


E: Failed to fetch http://218.189.123.38:80/videoplayer/libgegl-0.3-0_0.3.4-1ubuntu2_amd64.deb?ich_u_r_i=a511224256d2b18cd8cd0e2bd8dbed8e&ich_s_t_a_r_t=0&ich_e_n_d=0&ich_k_e_y=1945108917750363192466&ich_t_y_p_e=1&ich_d_i_s_k_i_d=6&ich_s_e_q=693606427&ich_u_n_i_t=1  403  Forbidden


E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?



```

I have tried:
1.apt update
2.apt update --fix-missing
3.change source
4.restart container
5.using PPA

But these method worked only occasionally.

How can I fix it?

Thanks&#65281;

---

### Post by cruzer001 on 2019-10-17
#5
Are you using a PPA? then just disable it.
```
software-properties-gtk
```
Should be in your sources list?
```
cat /etc/apt/sources.list && ls /etc/apt/sources.list.d/*.list
```

---

