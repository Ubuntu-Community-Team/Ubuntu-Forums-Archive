---
title: "wget cannot resume download"
date: 2013-04-23
forum: General Help
---

### Post by 001neeraj on 2013-04-23
I consider this is the last hope to get the answer of the following question:
I usually download using **Wget in Firefox through Flashgot**. Wget is an excellent, amazing application. I opened the /tmp folder when wget was working, and copied the last section of flashgot-2.fgt file and saved in a text document. That commands are:

    ```
wget --trust-server-names -c -O PSY_GENTLEMAN_M_V_hd720.mp4 --directory-prefix=/home/aliyans/Downloads --referer=https://www.youtube.com/watch\?v=ASO_zypdnsQ     --user-agent=Mozilla/5.0\ \(X11\;\ Ubuntu\;\ Linux\ i686\;\ rv:19.0\)\ Gecko/20100101\ Firefox/19.0 http://r5---sn-gxap5ojx-h55e.c.youtube.com/videoplayback\?fexp=933100%2C916624%2C932000%2C932004%2C906383%2C916911%2C916910%2C902000%2C901208%2C919512%2C929903%2C925714%2C929119%2C931202%2C900821%2C900823%2C909419%2C911416%2C908529%2C904830%2C930807%2C919373%2C930803%2C906836%2C920201%2C929602%2C930101%2C930609%2C900824%2C912711%2C910075\&cp=U0hVS1dQVV9HUENONV9PSllBOmFfa29IbDQ4d3dX\&gcr=in\&upn=mtbgQuSf-CM\&id=o-AMm8QIXQDWZCQxDjPkiC4ds0ksn7OTvBOcKTFE2GXMJc\&expire=1366757026\&sparams=cp%2Cgcr%2Cid%2Cip%2Cipbits%2Citag%2Cratebypass%2Csource%2Cupn%2Cexpire\&ratebypass=yes\&ms=au\&source=youtube\&sver=3\&ipbits=8\&mv=m\&itag=22\&key=yt1\&ip=101.63.155.73\&newshard=yes\&mt=1366734743\&signature=76A17DFD2F8BA28B19853AB135E6187D64CDBE96.A813703B0A2E01E33B472C844D76C89B108FAB4B
```

    Then i paused download by pressing **CTRL+C**. Next, i manually opened a terminal and pasted that arguments after wget command. _***It worked and resumed the download successfully***_. Then i **restarted** the computer and pasted that commands again. But, it didn't resume and showed up an error:

    ```
Resolving r5---sn-gxap5ojx-h55e.c.youtube.com (r5---sn-gxap5ojx-h55e.c.youtube.com)... 115.254.121.208
Connecting to r5---sn-gxap5ojx-h55e.c.youtube.com (r5---sn-gxap5ojx-h55e.c.youtube.com)|115.254.121.208|:80... connected.
HTTP request sent, awaiting response... 403 Forbidden
2013-04-23 22:28:26 ERROR 403: Forbidden
```

    Wget cannot resume in this method(**after a restart**) unless i am passing download request from Firefox to wget through Flashgot.
    I request you to help me to solve the issue.

Thanks in advance,
Neeraj S

---

### Post by Lars Noodén on 2013-04-23
Your User-Agent string seems to have an unterminated quote.  That might be the problem.

---

### Post by 001neeraj on 2013-04-24
> **Lars Noodén said:**
> Your User-Agent string seems to have an unterminated quote.  That might be the problem.
I dont think it is right. Beacuse, how could i resume download before restart? I uses the same lines of commands before and after a restart. Problem arises only after the restart.

---

