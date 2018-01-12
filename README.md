# Coffee Coin

![N|Solid](http://www.paperboardpackaging.org/images/default-source/School-Logos/sjsu-primary-mark_web.png?sfvrsn=0)

>“Bitcoin gives us, for the first time, a way for one Internet user to transfer a unique piece of digital property to another Internet user, such that the transfer is guaranteed to be safe and secure, everyone knows that the transfer has taken place, and nobody can challenge the legitimacy of the transfer. The consequences of this breakthrough are hard to overstate.” - **Marc Andreesen**

Energy Efficient Blockchain Simulator for Research started by Sharan Duggirala and Siddharth Kulkarni of the Department of Computer Science in San Jose State University. This is a fork of the original collaboration, that I intend to work on personally and/or other open source contributors. This project is intended for three different sets of people: 

  - People curious about the performance of their own computer when mining on a simulated network.
  - People who want to **investigate** the change of certain conditions and the respective resulting change in miner efficiency. In fact our **research** results are briefly displayed in this documentation and further elaborated on in the two PDFs within the repository.  
  - People who may want to fork this into a **new cryptocurrency**. 
 
  
# How to Run the Program 

*To find out futher about the functioning of each of the Python files, please refer to the **BREAKDOWN** section.* 

First and foremost the *coffeecoin-server.py* should be running at all times. This will be a simple call as shown below: 

```sh
python coffeecoin-server.py
```
Now we are ready to run the miners for experimentation. In order to make this easier, we have created an automatic miner, coded within *coffeecoin-autominer.py*. This can be called as shown below: 

```sh
python coffeecoin-autominer.py 4 1 
```
Here the arguments to the miner, are as follows: 

- **Argument 1**: The number of desired miners to be run on the computer
- **Argument 2**: The type of hashing function to be used. *1*,*2* and *3* signify *MD5*, *SHA1* and *SHA256* respectively. 

While stats are available from the *coffecoin-server*, use *coffeecoin-board.py*, for a better analysis. Execute this program as shown below: 

```sh
python coffeecoin-board.py
```

# Breakdown 

The project is divided into sections according to the division of the **Python** files within the code. 

- coffeecoin-server.py: The  server  program  is  designed  to  process  requests  and deliver data to users and miners over the entire block chain network. The functionality of the server can best be describedby the various routes through which requests are made and data is sent and received.
    -  *Transactions  Manager*: This  route  is  called  whenever  a  new  transaction  has  been  made  between  two  users.This  transaction  is  then  added  to  a  queue  of  unverified transactions, which waits till it is verified by miners.
    -  *mine - Mining Hash Verification*: This route is called when a miner sends an answer for verification. On successful verification,  a  new  global  challenge  is  set  and  the  miner  is awarded with a coin.
    - *info - Get current Hash challenge*: This route is used to receive information about the current challenge. Also newminers  are  added  to  the  list  of  miners  that  resides  on  theserver. This serves the purpose of deciding future challenges.
    -  *board - Get coins earned by each miner*: This route returns the data of coins earned by each miner, up until the time the request was made.
    -  *blocks  -  Internal  function  call*: This  route  is  aninternal function call, that returns the blocklist i.e all blocks connected to the blockchain to the network.
    -  *printblocks*: This is a debugging route that is used for  returning  and  displaying  information  of  all  the  blocks currently on the blockchain.

For an in-depth understanding of the various Python files within CoffeeCoin please refer to the *BlockchainEnergyEfficiciency.pdf*, titled **Randomized  Approach  to  Finding  the  Optimal  Blockchain  Miner Configurations  for  Maximum  Energy  Efficiency**. Furthermore, to understand the literature survey that has taken place in order to create this entire project, please refer to the *Energy_Efficiency_Survey.pdf*, titled **A Literature Survey of Energy Efficiency Within Blockchain Networks**. Both these documents are available within the repository, and we recommend at least a cursory glance through the first one. 
 
### Todos

 - Write more tests
 - Start building a UI

![Coffee](https://cdn.pixabay.com/photo/2017/08/07/22/57/coffee-2608864_1280.jpg)

License
----

MIT
