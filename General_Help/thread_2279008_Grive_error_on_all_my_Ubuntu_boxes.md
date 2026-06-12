---
title: "Grive error on all my Ubuntu boxes"
date: 2015-05-20
forum: General Help
---

### Post by ahounsome on 2015-05-20
Hi Guys,
can someone please help. Grive has broken on all my Ubuntu 14.04 LTS boxes with the following error:-
> Reading local directories
Synchronizing folders
exception: /build/buildd/grive-0.2.0/libgrive/src/http/CurlAgent.cc(149): Throw in function long int gr::http::CurlAgent::ExecCurl(const string&, gr::http::Receivable*, const gr::http::Header&)
Dynamic exception type: boost::exception_detail::clone_impl<gr::http::Error>
std::exception::what: std::exception
[gr::expt::MsgTag*] = 
[gr::http::CurlCodeTag*] = 0
[gr::http::HttpResponseTag*] = 400
[gr::http::UrlTag*] = [https://docs.google.com/feeds/default/private/full/-/folder?max-results=50&showroot=true](https://docs.google.com/feeds/default/private/full/-/folder?max-results=50&showroot=true)
[gr::http::HeaderTag*] = Authorization: Bearer ya29.eQEAqclq9-zCGN1FPeXpJCu-Tr9nn9w43vmpDcE0heEuoclnZANyrqOTDFZ2Hipku9s7ZDa-vZV1ig
GData-Version: 3.0


---

### Post by dino99 on 2015-05-20
grive is into the archive but cant find libgrive (neither a dependency)

---

### Post by ahounsome on 2015-05-20
Thanks Dino99, any idea how to fix this?
Thanks,
Andy

---

### Post by sandyd on 2015-05-20
Project is dead and broken due to API updates.
[http://askubuntu.com/questions/611801/grive-sync-error-possibly-google-api-shift](http://askubuntu.com/questions/611801/grive-sync-error-possibly-google-api-shift)

---

