---
title: "firefox proxy &quot;no proxy for&quot; issue"
date: 2015-05-21
forum: General Help
---

### Post by squarethumps on 2015-05-21
Hello,

I use ubuntu 14.04 at work for my work desktop.  They have a proxy server which filters all of our web traffic with the exception of an external mail server that is able to be directly accessed without going through the proxy.  As a matter of fact, the proxy server blocks it.  Why ?  I don't know .. that's just how the IT Nazis set it up.

Anyway, I have properly configured my proxy setting in firefox to use the proxy server for all web traffic, and it works fine.  Google, news sites, etc etc .. ALL work fine with the exception of those questionable websites that the proxy refuses for good reason ( pr0n, enternainment, gaming .. etc ) so everything is working nicely with that.

In my exception list ( No Proxy For ), I have listed the website of the external mail server that I use to access web mail, but when I have the proxy turned on, firefox still seems to be trying to route this web site through the proxy server because I'm getting a "Proxy Server is Refusing Connections" error.  I would say there's something wrong with the proxy, except when I completely turn off the proxy in the firefox settings I can access this external web mail server.   Of course when I turn off the proxy, none of the other websites are allowed through the regular network, so I get a Connection Refused error.   

So what could be happening that firefox still seems to be trying to use the proxy, even though the website is in the exception list ?   ( Yes, I've added numerous variations of the external mail server that I'm accessing, including the _exact_ address even with the https: portion ).  This makes no sense to me.  The prefs.js file does have the list of exceptions that I've entered correctly.   Obviously "the_server" below has been changed to protect the guilty. 

user_pref("network.proxy.no_proxies_on", "localhost, 127.0.0.1,mail.the_server.us*,*the_server.us*,https://mail.the_server.us/");

Any ideas on this ? 

Many Thanks

---

### Post by QDR06VV9 on 2015-05-21
Hi squarethumps
The first thing I would do is get the "IT Nazis" to set it up.
See If they permit you to just turn off the proxy(meaning noproxy setting in firefox) while trying to access those sites with the No Proxy Error!
Or Other unwanted adware programs might get installed without the user’s knowledge.(Possible)
And See here I sure you are aware of this but [https://support.mozilla.org/en-US/kb/advanced-panel-accessibility-browsing-network-upda?redirectlocale=en-US&redirectslug=Options+window+-+Advanced+panel](https://support.mozilla.org/en-US/kb/advanced-panel-accessibility-browsing-network-upda?redirectlocale=en-US&redirectslug=Options+window+-+Advanced+panel)
And this looks interesting [http://www.postseek.com/meta/33ed911db7e611ba0634a21705d47b4b](http://www.postseek.com/meta/33ed911db7e611ba0634a21705d47b4b)
Sorry not much help at the moment but maybe someone will jump in and get this going.
Best regards

---

