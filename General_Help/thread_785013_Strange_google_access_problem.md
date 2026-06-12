---
title: "Strange google access problem"
date: 2008-05-07
forum: General Help
---

### Post by lotrcz on 2008-05-07
After I did upgrade software for ubuntu 7.10.  I can't access google.com any more. Strangely, I can access google from another windows machine behind the same router.

Here is the javascript error I got when accessing google.com:
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
window.google={kEI:"cDghSMGWIozYoASLgqmwAg",kEXPI:"17259,17735",kHL:"en"}; function sf(){document.f.q.focus()} window.clk=function(b,c,d,e,f,g){if(document.images){var a=encodeURIComponent||escape;(new Image).src="/url?sa=T"+(c?"&oi="+a(c):"")+(d?"&cad="+a(d):"")+"&ct="+a(e)+"&cd="+a(f)+(b?"&url="+a(b.replace(/#.*/,"")).replace(/\+/g,"%2B"):"")+"&ei=cDghSMGWIozYoASLgqmwAg"+g}return true}; window.gbar={};(function(){var c=window.gbar,e,g,h;c.qs=function(a){var d=window.encodeURIComponent&&(document.forms[0].q||"").value;if(d)a.href=a.href.replace(/([?&])q=[^&]*|$/,function(f,b){
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>

I tried:
>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
wget [www.google.com](www.google.com)
 wget [www.google.com](www.google.com)
--22:22:02--  [http://www.google.com/](http://www.google.com/)
           => `index.html'
Resolving [www.google.com](www.google.com)... 208.67.219.230, 208.67.219.231
Connecting to [www.google.com|208.67.219.230|:80](www.google.com|208.67.219.230|:80)... connected.
HTTP request sent, awaiting response... 


>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>>
It just hangs.

If it is router or dns problem, I shouldn't be able to access from any machine behind the router.  But I can access google.com from any other machine behind the router.  That means router and opendns are working ok.

Only thing I can remembered was that when doing the upgrade, I had firefox google.com page open, then I noticed some script error on some windows on google.com.  After that, I have been experiencing the google.com access problem.  Does the upgrade screw up anything?  It shouldn't, right?

I am confused.  I am not sure what is going on here.  Any input would be greatly appreciated.

---

### Post by lotrcz on 2008-05-07
I got it working now.  

Here is what I did:

Synaptic---> search "firefox", remove it.  Then Install it back.

now google.com is ok.  

It is way too strange.  I have no idea why it isn't working, nor it is working now.

---

