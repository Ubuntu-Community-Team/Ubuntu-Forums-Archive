---
title: "Gnucash not updating Mutual Fund NAV since June 9 2017"
date: 2017-06-18
forum: General Help
---

### Post by kagashe on 2017-06-18
I am from India and have some Mutual Funds Investments and I have set up the Price Editor to fetch the rates from Association of Mutual Funds in India.[https://www.amfiindia.com]("https://www.amfiindia.com") It was working well till June 8 2017. Since June 9 it is giving error:
Unable to retrieve guotes for these items:
> MF:INF846K01EW2
MF:INF209K01YY7
and lists all codes

If I go the website it has the complete data.

Kamalakar

---

### Post by hari.m on 2017-07-23
Hi,

The old url for getting the stock data does not work anymore. The perl file IndiaMutual.pm has to be changed to take the changed url. 

I was able to get the prices by changing the url as follows within this file 

> $AMFI_URL = ("http://www.amfiindia.com/spages/NAVAll.txt");

Hari

---

### Post by kagashe on 2017-07-23
> **hari.m said:**
> Hi,

The old url for getting the stock data does not work anymore. The perl file IndiaMutual.pm has to be changed to take the changed url. 

I was able to get the prices by changing the url as follows within this file 



Hari
Thank you Hari.
I knew the location of IndiaMutual.pm but for others who may not know this is what I did:
```
$sudo cp /usr/share/perl5/Finance/Quote/IndiaMutual.pm /usr/share/perl5/Finance/Quote/IndiaMutual.pm.backup
$gksudo gedit /usr/share/perl5/Finance/Quote/IndiaMutual.pm

```
and changed the URL as suggested by you.

It works.
Thanks again.

Kamalakar

---

