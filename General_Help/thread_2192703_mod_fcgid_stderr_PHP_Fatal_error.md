---
title: "mod_fcgid: stderr: PHP Fatal error"
date: 2013-12-09
forum: General Help
---

### Post by martinmcanespie on 2013-12-09
I have a Ubuntu 12.04 Lamp server which i optimized 2 weeks ago for magento, from what i can remember i installed APC, memcache and made some cache tweaks in my .htaccess file in order to make my website faster by using the cache more

However recently when a credit card payment is made on my website, once the payment is authorized and redirects back to my website the user sees a blank page instead of the order confirmation page and the order does not complete.

However if i flush the magento store cache the error is fixed and payments complete as normal

Looking at my apache error log i can see

> [warn] [client xxx.xxx.xxx.xxx] mod_fcgid: stderr: PHP Fatal error:  Maximum execution time of 30 seconds exceeded in /var/www/clients/client1/web1/web/lib/Zend/Cache/Backend/File.php on line 747, referer: [https://.sagepay.com/gateway/service/authentication?action=callback](https://.sagepay.com/gateway/service/authentication?action=callback)

However this is a dedicated server so it shouldn't time out past 30 seconds - i can increase the timeout however i don't believe this is the main fault

In my modsec_audit.log

> --3a9bfb30-A--
[09/Dec/2013:10:23:28 +0000] UqWaAn8AAQEAAH9KQEgAAAAL xxx.xxx.xxx.xxx 24970 192.168.1.200 443
--3a9bfb30-B--
GET /sgps/formPayment/success/vtxc/SO00005139-2013-12-09-10-22-10/?crypt=@538db4927afeea77d3185ad99cbc942c7a2a06ba49ade2e9dc0e3df63978d842d9d41f7840cfddeffd9785212d2e6c1c0d915d102099b1f5ff2e89b67fb6b035658d7a70ac4e42a374bbb8909a93a808a00f391ced065b663d7db4dfc0d335ab178d48c7bb9b8c00acaac2c41943806b5a6264d893d70f6646a28596c76d2d99adc2bbbd7d69555eaed1287b799d7ca56e56a90536e4dac9a4a1319025c33a29d946e3829988384a4dada1c6db6353287bb3e05039fa0fa37fc328bf03c4f5a060c0f69243f705e3ddc345ec3bacf23ca2a1463ed78dfb2831af0043b846b0faf65a50307bc6819816bd567b51d5605d2c59fcebbaf0d80a4e61f35e17a2277c925324fcb9f47104052bef7af0b0a2bd148c3559b8c1cc3e9350deb9412407855ef69b60d65bc1af2d10795a01fe7e07b67cd75a43288ea1bfc6903ae0f8768f58d72eb5a672ff076e45ec8ac4aefdc40041bed6bc1efd22d0442fc1f27bb0591301e347205cb01d550697614ea0f13c3c2d16c11c79414ad826456a7b73977e792dfd9541bc16ad220221e53c1bb6cd HTTP/1.1
Host: mywebsite.com
User-Agent: Mozilla/5.0 (Windows NT 6.1; WOW64; rv:25.0) Gecko/20100101 Firefox/25.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: en-US,en;q=0.5
Accept-Encoding: gzip, deflate
Referer: [https://test.sagepay.com/gateway/service/authentication?action=callback](https://test.sagepay.com/gateway/service/authentication?action=callback)
Cookie: __atuvc=221%7C20%2C336%7C21%2C115%7C22%2C48%7C23%2C87%7C24; Drupal.toolbar.collapsed=0; Drupal.visitor.name=user%20test; Drupal.visitor.mail=user%40useremail.co.uk; Drupal.tableDrag.showWeight=0; external_no_cache=1; frontend=cnib30iqocf0f29b7d27rm75g1; adminhtml=o4fvnhts65p3gh1aku2p28oob6
Connection: keep-alive
Pragma: no-cache
Cache-Control: no-cache

--3a9bfb30-F--
HTTP/1.1 500 Internal Server Error
X-Powered-By: PHP/5.3.10-1ubuntu3.8
Expires: Thu, 19 Nov 1981 08:52:00 GMT
Cache-Control: no-store, no-cache, must-revalidate, post-check=0, pre-check=0
Pragma: no-cache
Set-Cookie: frontend=cnib30iqocf0f29b7d27rm75g1; expires=Mon, 09-Dec-2013 11:22:58 GMT; path=/; domain=mywebsite.com; httponly
Connection: keep-alive, close
Vary: Accept-Encoding
Content-Encoding: gzip
Content-Length: 20
Content-Type: text/html

--3a9bfb30-H--
Apache-Error: [file "fcgid_bucket.c"] [line 152] [level 4] mod_fcgid: stderr: PHP Fatal error:  Maximum execution time of 30 seconds exceeded in /var/www/clients/client1/web1/web/lib/Zend/Cache/Backend/File.php on line 747, referer: [https://test.sagepay.com/gateway/service/authentication?action=callback](https://test.sagepay.com/gateway/service/authentication?action=callback)
Apache-Handler: fcgid-script
Stopwatch: 1386584578248468 30409490 (- - -)
Stopwatch2: 1386584578248468 30409490; combined=238, p1=212, p2=18, p3=0, p4=0, p5=7, sr=52, sw=1, l=0, gc=0
Producer: ModSecurity for Apache/2.6.3 ([http://www.modsecurity.org/);](http://www.modsecurity.org/);) OWASP_CRS/2.2.8.
Server: Apache

Can anyone point me in the right direction to try and find out what is causing this?

---

### Post by SeijiSensei on 2013-12-09
> **martinmcanespie said:**
> However this is a dedicated server so it shouldn't time out past 30 seconds - i can increase the timeout however i don't believe this is the main fault

Usually that's a symptom of some problem in the code.  I've written some scripts that hit the time out limit when they got caught in an infinite loop.  I don't use any of the things you installed, so I cannot say much else about the source of the problem.  Did you look at line 747 in File.php referenced by the error and the code surrounding it?

---

### Post by martinmcanespie on 2013-12-10
I removed some of the cache settings in the .htaccess file and no problems for the last 24 hours

So i'll give it a few days and monitor the situation

Suspected code:

> #ADD KEEP ALIVE
#<IfModule mod_headers.c>
#   Header set Connection keep-alive
#</IfModule>
############################################
#CACHE STATIC CONTENT
## EXPIRES CACHING ##
#<IfModule mod_expires.c>
#ExpiresActive On
#ExpiresByType image/jpg "access 1 month"
#ExpiresByType image/jpeg "access 1 month"
#ExpiresByType image/gif "access 1 month"
#ExpiresByType image/png "access 1 month"
#ExpiresByType text/css "access 1 month"
#ExpiresByType application/pdf "access 1 month"
#ExpiresByType text/x-javascript "access 1 month"
#ExpiresByType application/x-shockwave-flash "access 1 month"
#ExpiresByType image/x-icon "access 1 month"
#ExpiresDefault "access 7 days"
#</IfModule>
## EXPIRES CACHING ##

############################################
#Compress Images
#<ifModule mod_gzip.c>
#mod_gzip_on Yes
#mod_gzip_dechunk Yes
#mod_gzip_item_include file .(html?|txt|css|js|php|pl)$
#mod_gzip_item_include handler ^cgi-script$
#mod_gzip_item_include mime ^text/.*
#mod_gzip_item_include mime ^application/x-javascript.*
#mod_gzip_item_exclude mime ^image/.*
#mod_gzip_item_exclude rspheader ^Content-Encoding:.*gzip.*
#</ifModule>
############################################

---

