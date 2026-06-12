---
title: "SSL configuration help"
date: 2014-02-09
forum: General Help
---

### Post by Alexander_Smith on 2014-02-09
Hey guys,  I need a bit of help on this one not to sure what the error is. 
Here is what i am trying to do is to enable ssl on mysql running on a ubuntu x64 server. 
I followed instructions on how to get ssl to work so i generated all files: 
6 files 2: certs, 2 keys, 2 ca 
Now when I edit the my.cnf and enter the lines :  
ssl 
ssl-ca=/etc/mysql/ca-cert.pem  
ssl-cert=/etc/mysql/server-cert.pem  
ssl-key=/etc/mysql/server-key.pem   

when i restart the service  my ssl variables look like this:  
+---------------+----------------------------+ 
| Variable_name | Value                      | 
+---------------+----------------------------+ 
| have_openssl  | DISABLED                   | 
| have_ssl      | DISABLED                   | 
| ssl_ca        | /etc/mysql/ca-cert.pem     |
 | ssl_capath    |                            | 
| ssl_cert      | /etc/mysql/server-cert.pem |
 | ssl_cipher    | ALL                        |
 | ssl_key       | /etc/mysql/server-key.pem  | 
+---------------+----------------------------+

  if i change the my.cnf to say only:  

ssl  

I get this:  +---------------+----------------------------+ | 
Variable_name | Value                      | 
+---------------+----------------------------+
 | have_openssl  | YES                        |
 | have_ssl      | YES                        |
 | ssl_ca        |                            | 
| ssl_capath    |                            |
 | ssl_cert      |                            | 
| ssl_cipher    | ALL                        |
 | ssl_key       |                            |
 +---------------+----------------------------+  

The only step I was not sure what to enter was a challenge password witch i did enter one so do i need to enter an extra line with that info? 
Or I am doing something else wrong. 
Hope this question is well explained please ask me to elaborate anything you need to know o help me resolve the problem. 

 Thank you

---

