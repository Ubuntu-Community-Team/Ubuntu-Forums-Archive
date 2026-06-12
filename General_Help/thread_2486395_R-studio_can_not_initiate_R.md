---
title: "R-studio can not initiate R"
date: 2023-04-28
forum: General Help
---

### Post by mohonpaul on 2023-04-28
I have installed R in Ubuntu 22.04 from official repository. But after installing R-Studio package from official website, it is not working stating that openssl version 1.1 is not found. Although I checked the openssl version and it is installed properly.

below I am submitting problem report.

## R Session Startup Failure Report

### RStudio Version

RStudio 2023.03.0+386 "Cherry Blossom " (3c53477a, 2023-03-09) for Ubuntu Bionic

Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) rstudio/2023.03.0+386 Chrome/108.0.5359.179 Electron/22.0.3 Safari/537.36

### Error message

[No error available]

### Process Output

The R session exited with code 1. 

Error output:

```
/usr/lib/rstudio/resources/app/bin/rsession: /usr/lib/x86_64-linux-gnu/libcrypto.so.1.1: version `OPENSSL_1_1_1' not found (required by /usr/lib/rstudio/resources/app/bin/rsession)

```

Standard output:

```
[No output emitted]
```

### Logs

*Log File*

```
[No logs available]

Any Idea ? What should I do now ?

---

### Post by monkeybrain20122 on 2023-04-30
```
RStudio 2023.03.0+386 "Cherry Blossom " (3c53477a, 2023-03-09) for Ubuntu Bionic
```

Looks like you downloaded the wrong deb.

You should get the Ubuntu 22 deb instead of Ubuntu 18+ [https://posit.co/download/rstudio-desktop/](https://posit.co/download/rstudio-desktop/)

I know, 18+ should include 22 but this is not the case here.

---

