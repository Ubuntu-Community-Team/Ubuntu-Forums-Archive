---
title: "Wondering if I can use Ubuntu desktop to facilitate Multi-Factor authentication"
date: 2016-09-07
forum: General Help
---

### Post by DVD-R on 2016-09-07
Hi All,
Please let me know if this is not the correct forum to post this question.

I believe Ubuntu desktop can easily do SMS text messaging service.
I have a skype account and the Skype app in Ubuntu works find for text messages.

Text messaging is one of the acceptable methods for Multi-Factor Authentication.

Has anyone utilized the text messaging functionality of Ubuntu for Multi-factor Authentication?
I would assume I need to invest in a text messaging service provider?

Sincere Thanks!
Got_Ubuntu!  :-]

---

### Post by TheFu on 2016-09-07
> **DVD-R said:**
> 
Text messaging is one of the acceptable methods for Multi-Factor Authentication.


Actually, using SMS is **not** an acceptable method to use for 2FA.  There are numerous attack vectors.  The US-Govt released new guidance recently prohibiting the use of SMS for 2FA.
[https://pages.nist.gov/800-63-3/sp800-63b.html](https://pages.nist.gov/800-63-3/sp800-63b.html)
and
[http://www.securityweek.com/nist-denounces-sms-2fa-what-are-alternatives](http://www.securityweek.com/nist-denounces-sms-2fa-what-are-alternatives)

---

### Post by Impavidus on 2016-09-08
Over here, all major banks require password+SMS as authentication for online banking. It never struck me as much more secure than password only, so it's best to have a really strong password and a secure computer. It may make things slightly more secure for those people who have weak passwords. The amount of fraud doesn't seem excessive, or the banks would have switched to something more secure – I hope.

Or the banks allow you to use some mobile app, which gives me the impression that a hacker only has to gain access to one device to steal from your account. I never used those.

Conclusion: The fact that professional organisations use something "for security" doesn't mean it's effective. They may just want to give the impression that they care about security.

---

### Post by TheFu on 2016-09-08
* never use any smartphone "app" to access any financial information. Good reasons that cannot be stated.
* Find a bank that uses 2FA based on a separate token.  Just ask. Mine sent one out the following day.
* Banks showing images as a security measure are clueless. That is just to make dumb consumers _feel_ better, without providing any real security.
* If/when your bank asked those 10 extra questions about your dog, marriage, grandparents - - - LIE!!!!!!  Don't ever tell the truth that someone else could discover. 
* SMS is not secure. Actually, the phone network is not secure. NEVER TRUST IT (even if YOU run the network).

Some banks require personal certs be installed to do online business. This is helpful, but hardly 100% secure.  It just means that the attackers need to use your system to gain access.

The best advice I have for online banking is to use a live-boot Linux distro running off read-only media (CD/DVD/ISO file in a VM).  Use it for 1 purpose and reboot. Don't visit your bank, then a brokerage site under the same boot. Always reboot between websites.  [http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/](http://krebsonsecurity.com/2012/07/banking-on-a-live-cd/) and [http://krebsonsecurity.com/online-banking-best-practices-for-businesses/](http://krebsonsecurity.com/online-banking-best-practices-for-businesses/)

---

