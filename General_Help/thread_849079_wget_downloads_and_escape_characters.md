---
title: "wget downloads and escape characters"
date: 2008-07-04
forum: General Help
---

### Post by vivek.shah_83 on 2008-07-04
hi,

i need to download a site with the following URL:

[http://www.ecch.com/casesearch/product_details.cfm?id=41443&rc=1&pg=1&tc=1&adv_search=1&adv_search=1](http://www.ecch.com/casesearch/product_details.cfm?id=41443&rc=1&pg=1&tc=1&adv_search=1&adv_search=1)

when i use wget for the download on Windows Vista, i get the following message:
[B][I]
--13:08:21--  [http://www.ecch.com/casesearch/product_details.cfm?id=41443](http://www.ecch.com/casesearch/product_details.cfm?id=41443)
           => `product_details.cfm@id=41443'
Resolving [www.ecch.com](www.ecch.com)... 138.250.12.12
Connecting to [www.ecch.com|138.250.12.12|:80](www.ecch.com|138.250.12.12|:80)... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]

    [  <=>                                ] 22,615        69.19K/s

13:08:22 (68.86 KB/s) - `product_details.cfm@id=41443' saved [22615]

'rc' is not recognized as an internal or external command,
operable program or batch file.
'pg' is not recognized as an internal or external command,
operable program or batch file.
'tc' is not recognized as an internal or external command,
operable program or batch file.
'adv_search' is not recognized as an internal or external command,
operable program or batch file.
'adv_search' is not recognized as an internal or external command,
operable program or batch file.
[/I][/B]

can you please let me know how do i work around this?

really would appriciate the help
regards,
vivek

---

### Post by Gunman1982 on 2008-07-04
Use "" or '' for the url.
Examples:
wget "weired url with many strange characters"
wget 'weired url with many strange characters'

---

### Post by vivek.shah_83 on 2008-10-03
hi,

i tried doing that as well, as in using the " and the ' quotes. it still gives the same error.

surprisingly, it is changing the ? to a @.

i tried wget-ing a google result page for the query on 'test':

[B]C:\Users\vivek>wget "http://www.google.co.in/search?hl=en&client=firefox-a
&rls=org.mozilla%3Aen-US%3Aofficial&q=test&btnG=Search&meta="
--15:37:54--  [http://www.google.co.in/search?hl=en&client=firefox-a&rls=org.mozi](http://www.google.co.in/search?hl=en&client=firefox-a&rls=org.mozi)
lla%3Aen-US%3Aofficial&q=test&btnG=Search&meta=
           => `search@hl=en&client=firefox-a&rls=org.mozilla%3Aen-US%3Aofficial&
q=test&btnG=Search&meta='
Resolving [www.google.co.in](www.google.co.in)... 209.85.153.104
Connecting to [www.google.co.in|209.85.153.104|:80](www.google.co.in|209.85.153.104|:80)... connected.
HTTP request sent, awaiting response... 403 Forbidden
15:37:56 ERROR 403: Forbidden.[/B]


can anybody suggest if this is a windows OS issue or i need to do something more in escaping the charecters?

cheers,
v

---

### Post by Sycron on 2008-10-03
403 means Acces denied.

---

