---
title: "user:group directory privileges"
date: 2022-08-27
forum: General Help
---

### Post by ghoulie on 2022-08-27
Hello all, 

I have a small privileges problem with my media server. I have 2 users named docker and media. 
docker has directories for jellyfin which contains config files in it. 
media has movie serial and mp3 directories. 

docker and subdirectories privileges are rwx/r-x/---
media and subdirectories privileges are rwx/r-x/---

when I try to add the movies to jellyfin app on web browser. The app can't add the movies inside the directory. If I set the others privileges the app adds the movies to libraries. 
I created a multimedia group and added docker and media users in it but still I have to give privileges to others. It is same for the other directories. If I am not wrong when I set docker:multimedia and media:multimedia both users and directories have access for each others. I hope I could explain what I mean. I am newbie on linux. Looking forward to your helps. 

the distro is ubuntu server 22.04 lts

[IMG]https://ubuntuforums.org/attachment.php?attachmentid=290934&stc=1[/IMG]
[IMG]https://viewer.diagrams.net/?tags=%7B%7D&highlight=0000ff&edit=_blank&layers=1&nav=1&title=server.png#R7Vvfc5s4EP5rPHP3EAYQGPwYx07bmXYuc%2Blcm3vJYJCxGkCcEIl9D%2Fe3nwTip7CNU2wnafAkRgus0H7fSquVPAJX4foDceLVF%2BzBYKSr3noEZiNd13R1wr64ZJNLxsDKBT5BXi5SK8Et%2BheKJwtpijyYCFkuohgHFMVNoYujCLq0IXMIwU%2FN25Y48BqC2PGhJLh1naCQKmYl%2F4Y8usrl%2BqR2%2F0eI%2FJWo29BAfmHhuA8%2BwWkkKoxwBPMroVNoEY1MVo6Hn2oiMB%2BBK4Ixzc%2FC9RUMuF1bJkvopnjPEZiuaBiwgsZOs8vXWx7W%2BjzM2kVgROvVbdM3m8yTGH4zH43bD%2BuPtmau5n9fAIH7oxOkRS3tahNK8ENpVF51aQiVFTwnWUFPFJwA%2BRE7d9lLQdJ8YfZUzFWGa5%2BTUAmx%2B5DGCqMEdVAESaIQknFjSgTBuMa89iscYJK9DhhnR2mAR0goXLe4UdlEK3Fi3Ic4hJRs2C3igbGdPyFYbwBBiqeKQZoqUFzV2KMZgm6O4K1fqq4QYCcChAMAMdS%2BgBQmQdEKEsTNtkRBIEuZsT3E7CFfOS%2BwS3ZZFDVLlLtgzu4Tjee1EZiwp%2Bpv3YsIO%2Bgv06OJv6LWD02mgy1AIzBwKHps9lTDU0R7p8iro4h1KEVEjTcYsdcreyir1e%2Fg5TKBVKJU%2BZ7PZ5luSiz7wR7bLFEks%2B0BUndV0IDpykb4JVpzbtRpEPPWZK9uTkfmrEaaAC45%2BijMBvoG8noln6HQZ60J0IK3KXEdNlRfzxiXIFGSR5%2FdGDgLGNzgBFGEuV6SQzDl0CMWL3xuXQ%2BR5%2FFmlDdcihcqLwxPnUKNrWh2%2FdMYi3RdAbY0GgFL0a36R2YaUBVzDGqfI3VD%2BlgiiINIgiPkvhPkBASZqC%2BZHfb%2BMQp6LIQXRUzoCvs4coJ5JZ1mYXk5vlT3fMY4FoT5ASndCCI4KcVdMTKvaHeAyN4Lp8SFOxokDEUd4sNdmFrdkJ4mNJBdMl2kEU15AyFhFJVAKPypZrQuV3IDFN87hPJTHMYpG%2BATdn6bKb3%2Fip%2FYf0231%2BxPiaMuPyujgm2ORjmmchDRdrsFphSHw4T%2FmtV0KVMO%2F%2B2O6L%2BQDQ6ftd9pyAqHi5RVPH1aIQpvYydj7ROLqpoobrVbBsy0nPUW8ZQHl04a0OMYVhuf2bLyNFdherKpe9vCrNW0Fbw2guksQdCMpIVoL3fLIaMLu2ZnNwQIdgsEW44nxh0ggGOBoPWY2zatsIfjAxiplQEARs8MwPhoRuoxuzu1kV6glWSH%2Fo8p8rJI7w27tAqaQJhndmlddmmOQwg95LxdGIBqvjAYjP2dBoy8S55pr6xaA6JpImYGsvleL9zxgmIWxdm6fnG2aZi2T7i9N4zWtiBQs7DZYWHzJ9MsRYfXmmsBCzRV5NMF8VQFnqxIbykyW4pyQ0iKBsvi9Mjvv86QUj93SAl6DNSH%2BNwa0e%2FiCj%2BveRwrVQ7HC4f7297praZ2W%2F80%2Fqa1A4xn%2B1vbcY1%2B%2FsZQcja120Qe6uAOoiJUrnFQZwZ652DL3Be%2B3bG2PYvRzz2LKdYIB%2Fb7ytfv6q5%2BbL%2FX9y9vnNDv9clAfq%2F39PuhXNN4VgBWLp9p%2FaKxKgC7K0aKQaKxvSwpVqX3h23nHUbULev5h9JJM1vdu31iOsmLbxKdXti2jPwYKN9QBG079mVYHYsbR4v1DDmxPtLHWWibxE7UAGb8T8o3BE3d3DaXnNb%2B4jf2aqxutfj6PbOUypexLp5EE%2Fithpq7bqGFnfniO6uOP9BZXaYpyQDieux43amHBwyqpl18%2BeOvT%2FNCKZPlept1MXHeukLcycDzbDIolu3exB6D3N139ppddC9WYE%2B07aRrdeIV%2B4B%2BcTv%2F89Pl53cneNVOAH4ydNg0fen4G2uMrqXxV%2BxH4OLLDRjEiV4m%2BZfZ0UH%2Buoez%2B66zY2do9ALc5eAxo9tdzJO5i9kVerXoc%2FgmBh8yOjis8ut5GNPN%2FTUOPGkLw3Ygt0E%2FPJxCzUTRwaR2NNcfdCk61oBijzvQP1ZwYPaYsPzyKE2KHymcE6geiYpfHShzcn6YnrW40DOfVGUcuY1qqw1qUexOO%2FLCDQtXWRN5EmHwJNN474h2xNwRaOeO9GfmjoDeSl6op80dmfIqgUQdaQtuXIOV1YHiBNaQrnNJSiVtj9RYyOeiyP%2BabdYEVS%2FS2Zs4Lgfv3kM8QsMcqes0YX2I47qMvTQR23eP1Insy0e1tl2MVcWS%2B3LdVPSuTsJQjvVrIbPHWsQ71gdhbVmKZci%2F5dix02NI2ItNibUeofrBJpj%2FDw%3D%3D[/IMG]

---

### Post by TheFu on 2022-08-27
I use jellyfin.  It follows standard Unix permissions, so you'll need to learn those.  Jellyfin only needs read access to media files for playback, BTW.   If you want it to be able to delete files, then jellyfin will need write on the directory containing the files.

I hate to say it, but you'll need 45 minutes of concentrated time to figure this stuff out. There's no shortcut.  But since every popular OS in the world today, except 1, uses the Unix permissions model, this is very useful information.

To get multiple users working together, reading and writing to the same files:  [Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp](Https://ubuntuforums.org/showthread.php?t=2382965&highlight=working+chgrp) has some steps. These are just an example, but if you need 2 userids to have full access to the same files, that's what you need.  A good understanding of Unix permissions is required. There are subtle things that will be missed and make things worse without the proper understanding.

It should go without saying, but before you apply this knowledge to all your media files, do it for just 1 directory and validate that it works.

BTW, images aren't needed.  The output from **ls -la** that includes the parent directory and sample files is what we need to see. Don't improvise. We know how to read that output. Use forum 'code tags' when posting shell/CLI commands with output so it is readable.

---

