---
title: "Firefox Not decting my internet"
date: 2006-11-25
forum: General Help
---

### Post by Magiczero on 2006-11-25
Hi Guys

When I open firefox I get this error:

> The proxy server is refusing connections

      

      
      
      

      
        
        

          

Firefox is configured to use a proxy server that is refusing connections.

        


        
        


    *   Check the proxy settings to make sure that they are correct.

    *   Contact your network administrator to make sure the proxy server is
          working.

I am not using a proxy to get online at all, I don't know what's wrong or how to fix it.  I have no certain I have to use to get online but I can not change the settings in firefox because I don't know how.  I have gone to > Edit<Prefrences<Advanced<Network<Settings and everything is grayed out.  Can I get help?

Thanks

---

### Post by steve.horsley on 2006-11-25
The only thing I can imagine that would grey out those settings would be if the settings directory was somehow not owned by you - so you only have read rights to the settings. Try closing firefos and then this command (substitute your real user name) and see if that fixes things:
**sudo chown -R Magiczero:Magiczero .mozilla**

---

