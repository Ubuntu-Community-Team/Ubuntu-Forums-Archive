---
title: "HOWTO: Read Webmail from any Mail Client using FreePOPs"
date: 2007-12-06
forum: General Help
---

### Post by Flare183 on 2007-12-06
**HOWTO: Read webmail from any email client with FreePOPs**

 					         					            You can send and receive messages from most Web-based email services with your favourite email client by using FreePOPs, a webmail access daemon.
					        
 						 					            Web-mail accounts can be annoying to work with, especially if you've got several with different service providers, all of whom offer non-standard user interfaces to get and send email. Some webmail services offer a free or extra-cost POP/SMTP (read: regular email) access option, but FreePOPs can help you avoid the extra-cost plans. In addition to providing a unified user interface for all your email accounts, it also offers:
  [LIST]
[*]*Off-line access* -- a feature missing by definition in webmail, but that may be critical if you're on the road.
[*]*Security* -- message encryption, decryption, and digital signing are, at best, awkward with webmail.
[*]*Local storage* -- email clients keep messages on your computer's hard drive, thus allowing you to back them up or search through them.
[*]*Common address book* -- no need to synchronise the address books on several webmail accounts with the one used by your email client.[/LIST]  FreePOPs has been around since mid-2004 and seems to be under active development. It's available for Linux, Unix, Mac OS X, and Windows.
  **Getting messages: A local POP server**

  Getting messages from a webmail service into your email client requires a program that can log in to your webmail account on your behalf, present itself to the webmail server as a regular Web browser, retrieve messages from the account, and hand them over to your email client via POP (Post Office Protocol). FreePOPs is just such a program. The core program handles the bits of functionality that are common to accessing all webmail services: POP3 server, HTTP client, HTML parser, etc. The details of how to work with each webmail service are handled by plugin scripts written in a programming language called Lua. FreePOPs comes bundled with plugin scripts that provide support for Gmail, Hotmail, Yahoo! Mail, mail.com, and others. You can download additional plugins that support additional webmail services.
  FreePOPs determines which script to run by looking at the account user name that's supplied to it by the email client. Thus in order to access your Hotmail account you need to specify your user name not as just username but as [email]username@hotmail.com[/email]. This method allows a single FreePOPs daemon to access any supported webmail service without the need to configure it in advance for a specific provider.
  You can install FreePOPs from most Linux distributions' package management repositories. Once it's installed you can run it as a service by running, as root, the command update-rc.d freepops defaults, which makes the FreePOPs daemon start automatically upon system startup. You can start the daemon manually with the command /etc/init.d/freepops start.
  The FreePOPs daemon listens for incoming connections on port 2000, so as not to interfere with a normal POP server (if installed). You can modify this behaviour, along with some other aspects, by editing the file /etc/default/freepops, but the defaults should work for you out of the box.
  Now you can configure your email client to receive messages from webmail accounts. I use Icedove, the unbranded version of Thunderbird. Add an account using the new account wizard. Specify localhost as the incoming mail server, and your email address as the user name (remember, use the full address). The wizard does not let you specify the incoming server port, so you have to edit the server settings after the account has been created and set the port number to 2000.
  If you already have a regular email account provided by your workplace or ISP, you might be able to use it to send your messages if that SMTP server is configured to *relay* messages -- that is, if it allows you to send a message with a different email address than the one you have registered with that server. My ISP allows that, but my workplace server does not.
  Another option is to use a locally installed SMTP server to send email messages. A typical Debian installation includes such a mail server -- exim4. In order to configure it for the job at hand, run the following as root:
  dpkg-reconfigure exim4-config
  This will walk you through a set of screens with options to select from. At the first screen, select the mail server configuration type to be "internet site; mail is sent and received directly using SMTP." With the rest of the options I selected the defaults that were presented to me, but your needs may be different. Read the on-screen instructions, and consult the relevant manual pages for exim4-config_files and update-exim4.conf.
  Once you have a usable SMTP server, go back to Icedove, select Edit -> Account Settings..., select Outgoing Server (SMTP), and press Add.... Set the server name to localhost and the user name to your local user name. Press OK, then go over each webmail account that you've created and at the account settings dialog select this server from the Outgoing Server (SMTP) drop-down list.
   **Caveats**

  While FreePOPs can make things more convenient for users, webmail service providers, in general, do not support the use of such tools. This becomes painfully obvious when a provider decides to upgrade or otherwise modify its webmail interface. The relevant FreePOPs plugin script may stop working as a result. If a fix already exists for the plugin, you can download and install it using the FreePOPs plugin update utility -- freepops-updater-dialog. Otherwise, the only option is to go back to the Web browser to access your account. Typically, though, these interruptions don't last long -- the FreePOPs community forums are quite active, and the developers are usually quick to fix such problems.
  Another issue crops up when sending you send messages from a local SMTP server: many receiving systems on the Internet block incoming messages from dynamic IP addresses in order to avoid spam, which often comes from servers on such addresses. This means that, in theory, you may experience some email delivery problems if you use a dial-up connection to access the Internet.
  Despite that, FreePOPs can make tracking your webmail traffic much simpler. The added hassle and occasional down time are, in my experience, minimal.

---

### Post by K.Mandla on 2007-12-20
Moved to General Help.

---

