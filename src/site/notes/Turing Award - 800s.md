---
{"dg-publish":true,"permalink":"/turing-award-800s/"}
---

[[2025-08-23\|2025-08-23]]


<div class="transclusion internal-embed is-loaded"><div class="markdown-embed">




==⚠  Switch to EXCALIDRAW VIEW in the MORE OPTIONS menu of this document. ⚠== You can decompress Drawing data with the command palette: 'Decompress current Excalidraw file'. For more info check in plugin settings under 'Saving'


# Excalidraw Data

## Text Elements
Origin 
m0 
Problem:
Replicate a 500GB file to 1000 Machines

1. Network IO each machine: R = 10GBit/s
2. File size: S = 500GByte
3. Destination machine number: N = 1000 
Solution 
Step 1: 
divide the file into N segments evenly
end up with F = f0 + f1 + ... f999

time = 0



Step 2:

Set up connections from origin machine to target machines. Each connection uses R/N IO









Step 3:
Set up connections between target machines
Each connection uses R/N IO

Taking m0 as example:
connect m0 to its next 499 neighbors, ie m1-m499














Step 4:

origin machine: streaming f0 to m0
m0: streaming f0 to m1-m499

behavior is same for all m0-m999 machine: 
m(n) writes to m(n+1) through m(n+499)


!!! All streaming tasks start and finish at the same time.


At completion, m0 receives f0 from origin machine,
receives f501-f999 from m501-m999

Total data on m0: S / 1000 * 500 = S / 2 = 250GBytes


Time is just the time used by origin machine to stream f0: (S / N) / (R/N) = 400s



Step 5:

repeat step 4, but stream f500 from origin to m0;
similarly, streaming f(n + 500) to m(n)

At completion, m0 received another 250GBytes

Time is same as Step 4 = 400s


Solution Total time: 800s 
f0 
m1 
f1 
m999 
f999 
m0 
Origin 
f0 
m1 
m499 
f0 
f0 
m501 
m999 
f501 
f999 
Origin has 1000 out connection 
m0 has 499 out connection;
500 in connection 


</div></div>



