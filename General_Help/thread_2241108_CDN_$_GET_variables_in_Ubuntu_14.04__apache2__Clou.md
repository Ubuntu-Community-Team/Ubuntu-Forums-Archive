---
title: "CDN $_GET variables in Ubuntu 14.04 / apache2 / Cloudfront ?"
date: 2014-08-24
forum: General Help
---

### Post by josh77 on 2014-08-24
cloudfront no support get and post

---------------



With Cloudfront CDN, $_GET and $_POST variables are not being set. It works great with direct IP access however.


I guess this is more a question of interoperability with the CDN, as it works great 




# with cloudfront 

$_SERVER['QUERY_STRING']
# completely empty, shows nothing

$example = $_GET['example'];
# also empty




It worked perfectly on my fedora test server, as it should (its maddening because there is basically no possible way that this could not be working).


I don't want to blame Ubuntu.. but I haven't seen this in any other distros... how to get this operating as expected, or should I spawn off a different flavor vps?

---

