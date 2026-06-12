---
title: "Problem to recover encryptfs"
date: 2017-04-04
forum: General Help
---

### Post by sergito23 on 2017-04-04
Hi 

I got a problem with ecrypts files. I sumarize this:
1.I drop for error the content of my /home
2. I trie to recover the data with Fhotorec
3. This process generates more than 1100 folders with any type of content, i.e. ecryptfs files
4. I trie to recover hte content of my home, by the process indicates below 
5. The files of my /home dont appear, just files likes the indicates below

I NEED HELP. THE PROCESS I EXECUTE DONT SHOW ME RESULTS


-----------------------------------------------

```
cd /home/sergio/.ecryptfs/ecryptfs-wrap-passphrase wrapped-passphrase
```
RESULTADO:
```
bash: cd: /home/sergio/.ecryptfs/ecryptfs-wrap-passphrase: No existe el archivo o el directorio

```

```
sudo ln -s /home/sergio/.Private OldPrivate  SE CREA ENLACE SIMBPOLICO DEL BACKUP AL ANTIGUO ARCHIVO .PRIVATE
```
```


sudo ecryptfs-add-passphrase --fnek
Passphrase:   SE OBTIENEN DOS CLACES ADICIONALES A PARTIR DE LA PASSPHRASE GUARDADA EN LA INSTALACI
```


RESULTADO

```

Inserted auth tok with sig [cd4b7903862b77be] into the user session keyring
Inserted auth tok with sig [2cddc2eaae0bd916] into the user session keyring
```


------------------


INICIO DEL BACKUP


```


/home/sergio# sudo mount -t ecryptfs OldPrivate oldHome
Passphrase: 
Select cipher: 
 1) aes: blocksize = 16; min keysize = 16; max keysize = 32
 2) blowfish: blocksize = 8; min keysize = 16; max keysize = 56
 3) des3_ede: blocksize = 8; min keysize = 24; max keysize = 24
 4) twofish: blocksize = 16; min keysize = 16; max keysize = 32
 5) cast6: blocksize = 16; min keysize = 16; max keysize = 32
 6) cast5: blocksize = 8; min keysize = 5; max keysize = 16
Selection [aes]: 
Select key bytes: 
 1) 16
 2) 32
 3) 24
Selection [16]: 
Enable plaintext passthrough (y/n) [n]: y
Enable filename encryption (y/n) [n]: y
Filename Encryption Key (FNEK) Signature [cd4b7903862b77be]: 
Attempting to mount with the following options:
  ecryptfs_unlink_sigs
  ecryptfs_fnek_sig=cd4b7903862b77be
  ecryptfs_passthrough
  ecryptfs_key_bytes=16
  ecryptfs_cipher=aes
  ecryptfs_sig=cd4b7903862b77be
WARNING: Based on the contents of [/root/.ecryptfs/sig-cache.txt],
it looks like you have never mounted with this key 
before. This could mean that you have typed your 
passphrase wrong.


Would you like to proceed with the mount (yes/no)? : y
Would you like to proceed with the mount (yes/no)? : yes
Would you like to append sig [cd4b7903862b77be] to
[/root/.ecryptfs/sig-cache.txt] 
in order to avoid this warning in the future (yes/no)? : no
Not adding sig to user sig cache file; continuing with mount.
Mounted eCryptfs


/home/sergio/temporal# ls
ECRYPTFS_FNEK_ENCRYPTED.FWYk-P6pdC6vD-RlW9MUPXuKrOcbRTKSz2P4DH-GSBBVe-GkvvnUX4WX9U--
ECRYPTFS_FNEK_ENCRYPTED.FWYk-P6pdC6vD-RlW9MUPXuKrOcbRTKSz2P4HHekSkw74Gje4mR4cnjk8---
ECRYPTFS_FNEK_ENCRYPTED.FWYk-P6pdC6vD-RlW9MUPXuKrOcbRTKSz2P4oH3Nq7f-Yr.lb5MMirAE5U--
ECRYPTFS_FNEK_ENCRYPTED.FWYk-P6pdC6vD-RlW9MUPXuKrOcbRTKSz2P4WdYo-a4FCtVAI5sGLaww6k--
ECRYPTFS_FNEK_ENCRYPTED.FWYk-P6pdC6vD-RlW9MUPXuKrOcbRTKSz2P4wQZccyUebPmnIirnhdFJJU--
ECRYPTFS_FNEK_ENCRYPTED.FXYk-P6pdC6vD-RlW9MUPXuKrOcbRTKSz2P4oAbZRc9z.XtA0sdAsouCOmH8R4zJ9OecfkNx85ab8-2-
```

---

