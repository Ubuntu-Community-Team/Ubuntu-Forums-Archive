---
title: "query NNTP TOR headers"
date: 2019-11-04
forum: General Help
---

### Post by perlman2 on 2019-11-04
Hi, all
I'v installed Ubuntu Linux dist and configuring NNTP throught TOR proxy
I'v tested and works fine, however the post revealed interesting new TOR related NNTP headers


I'd like to know how to query NNTP headers
Injection-Info:logging-data, X-Trace, NNTP-X-TOR-Router, NNTP-X-Ufhash, Content-ID


article-number	in Xref: newsgroup-server newsgroup-name:article-number


to get more info ?


any script/app/program/code on the net ?


thank's

---

### Post by #&amp;thj^% on 2019-11-05
Simple question, why over Tor?
Would a VPN work for you?
Last I saw, _[U]TOR seriously disapproves of bin traffic on the network_[/U].

When I upload, I usually use a VPN, and my posts complete just fine.

Don't know if you have seen this yet: [https://www.oreilly.com/openbook/linag2/book/ch22.html](https://www.oreilly.com/openbook/linag2/book/ch22.html)

Last I heard, there was no need to mask your traffic when using usenet, only torrenting.(Some of which is illegal to discuss here in the Forums)
And this is a heads-up only: (**Just informational only**)
> Usenet abuse is far from trivial.  There are a number of reasons why investigating Usenet evidence is difficult for a forensic analyst, and this is most likely why Usenet is such a popular tool for transmitting illegal content.   Among the difficulties that a forensic analyst may face in a Usenet investigation are the following: oInternet Anonymity.  Due to the fact that it is trivially easy to change the identification strings (such as the From: header), it will most likely be necessary go to Usenet providers for logging information, which they may or may not have kept.  These providers may be protected under the “safe harbor” laws, and argue that they simply allow access to content, and do not explicitly monitor what their users access or encourage illegal activity.

---

### Post by perlman2 on 2019-11-06
thank's for the [https://www.oreilly.com/openbook/linag2/book/ch22.html](https://www.oreilly.com/openbook/linag2/book/ch22.html) link but I have already throughly read that


I just want to get more info on those headers
Injection-Info:logging-data, X-Trace, NNTP-X-TOR-Router, NNTP-X-Ufhash, Content-ID


X-Trace comes in 2 formats, one with 1 long string composed of 2 up/down case /[a-zA-Z]/ and numbers /[0-9]/ string seperated by "/" == /[a-zA-Z0-9\/]/
and the other composed of a domain name (reader13.wxs.nl), a long integer (1046477701), a short integer (6515), an IP (62.131.195.7), and a date (1 Mar 2003 00:15:01 GMT)


Injection-Info:logging-data="74569"		# does not appear to be an article number since I tried to download using "GROUP 24hoursupport.helpdesk ; HEAD 74569" telnet NNTP command thought it worked for other number
X-Trace			: q8cNyBZr8H6vQw1XWBg3Lw/QBrMuMlRjgDz4A0vDV6dfOCokS6
X-Trace			: reader13.wxs.nl 1046477701 6515 62.131.195.7 (1 Mar 2003 00:15:01 GMT)
NNTP-X-TOR-Router	: 23.129.64.166		# not obvious if it is entry/middle/exit IP
NNTP-X-Ufhash		: YtJ30QQgcFxG4hLqNbDT%2FJUgmvQBaS2dMHPMMaCdTOYJqY%2FF2Z%2BpctlKOZehQJimaSE%2Bfq9mw%2FzLeJ5OrtUcBM%2F3hsuOMngxbDwLv8DlmlZNZCdUtBV7xl5VzF3O9QGsMLgB8YVRmpHb5cTzDKoOwZF69T1IDryKnTSJSi%2BslF6XYnLJEDgPSRbvKdNyXFMOqX0jfeMLVTg4YRvfeLP8Y%2FMFFMF16kAVKk0w		# can't decypher anything!
Content-ID		: <e4$28qqjmbe4$2jo3e4s545kSqDwSpdkf8q9$1@reader13.wxs.nl>


all the above identifiers must somehow be queryable ?


thank's in advance

---

### Post by #&amp;thj^% on 2019-11-06
I guess I missed the mark then, on Tor that's all you'll get to see.
That's the nature of Tor. 
VPN is suggested, and my choice. ;)

---

