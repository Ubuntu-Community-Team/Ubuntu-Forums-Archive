---
title: "openssl - version mismatch - supported 00 parsed 03"
date: 2016-12-06
forum: General Help
---

### Post by marchello_lippi2 on 2016-12-06
Hi all, 

Well, my question is not ubuntu-specific because I do receive this error under windows as well. Please put my topic into the appropriate thread if needed.

I'm about to use openssl to authorise from my ubuntu with third-part application (I work on it as freelancer).
Got openssl key from the previous freelance developer. 

His key looks like: 

```

4679 b02b 21e7 2d97 7bb8 bfc1 c8be 37f6
8623 cee6 0582 905a 6609 ca7f 2cf5 a3ed
13b1 5f68 d578 d690 f84a 38d5 bbf0 a902
8181 009f 5839 74d0 736a ca38 6315 2b95
1145 e689 7ccf 163a a169 84f9 8dcd 9645
de13 e5f5 bccd 45c9 9666 2f2e b1a3 e24c
16f1 9c90 484a 3ee5 6595 612a dac8 1657
d355 e813 683f 3fa9 bfc5 3cc9 7143 e975
35bf 3b7b 33ac 3773 3162 b642 de87 ac52
9cf7 cbfd baeb e603 d5e6 f6bd 1f2e 3dbf
d735 4a2c f9d1 2b9f f299 d209 b116 1587
36af 79

```
(77 lines total)

mine looks like: 
```

c303 17ec 54c9 953c a46f 40b8 73bb 44f8
4c60 881a d748 8c71 57e3 a818 d02b 7803
3909 d71a 8fe0 9944 a0a5 32e5 4b82 7b40
66b2 976e 20ae 2e2d b7c1 b927 58ac ee2c
5caf 1b14 6667 4ea7 38ed 89c9 18b6 541c
a7c0 4131 2530 2306 092a 8648 86f7 0d01
0915 3116 0414 1efa 8c9c 785b 29d6 e6b0
5272 873a 22b5 7637 cf59 3031 3021 3009
0605 2b0e 0302 1a05 0004 145e b785 02c8
8a9a 4409 264f 634a 51f7 aa6b eeeb 2604
0885 f16d 647c d0a6 5c02 0208 00

```
(110 lines total)

So, mine is likely of the same format, just bigger. 

Now I'm getting error 
```

java.security.spec.InvalidKeySpecException: Remote java.security.spec.InvalidKeySpecException: java.security.InvalidKeyException: IOException : version mismatch: (supported:     00, parsed:     03

```

Any suggestions how do I convert my key to "shorter" version or other solution? 
I tried to google it, this question is already discussed on different boards, but I did not find solution for making "shorter" key version. 
Please advise. 
Thanks ahead.

---

