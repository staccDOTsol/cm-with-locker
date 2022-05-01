# CM V2 With Candy Locker

## Proof of concept

Coming from web 2.0, users are only allowed to access their own data via passwords. 

### Current Problem with CM V2:
bots can access the mint through methods other than what is provided in the mint page. 

### Solution:
lock the mint with passwords only known to authority initialized after the cm v2 has been made using AES 256.


## Mechanism of the Candy Locker:
 * Initialize after the cm v2 is done
 * recieve a list of passwords, perferrably an alphanumeric 16+ character length string.
 * when minting, the transaction has to pass one password.
 * the rust code will loop through and find if the password is there.
 * otherwise mint will fail

##### Method of Encryption and Decryption?
Since it is an Open Source program, the encryption keys would be simple and public. The Encrypted Passwords that are stored in the Candy Locker account is public as well. Thus, maybe adding the candy locker should be done few minutes before the go_live_date, since brute forcing AES codes with 16+ characters will take at least a few hours to get one value.

##### Why AES 256? 
Fastest.

##### What about collision of passwords? 
Make (items_available * 3) amount of passwords and round robin through them. on the frontend. 

##### Where do we store the passwords? 
Somewhere safe. either in the code but you will need to obfuscate the JS in the frontend, a redis instance, firestore (firebase), or simply in the .env file.


##### What is done?
- [x] Provide proof of concept code in lib.rs of cm v2 for candylocker.
- [ ] Create JS code
- [ ] Upload to devnet for testing
- [ ] Final clean up for mainnet
- [ ] Upload to mainnet

#### Note:
Excuse my rusty rustlang code for the proof of concept. - CryptoMiester