**Hash map:** A *hash map* is a data structure that can map *keys* to *values*. It uses a *hash function* to compute an *index* (hash code) into an array of *buckets* or *chains*, from which value can be retrieved.

The algorithm for hash table involves two steps:
1. Compute the Hash Function.
2. Avoid Collisions.

**Hash function:** Hash function will assign unique key to a bucket, but hash function can generates the same index for more than one key, which leads to collisions.

The hash function used in this program is modular hashing.

```java
int hash = 0;
for (int i = 0; i < s.toString().length(); i++)
	hash = hash + s.toString().length()
hash %= M;
```

**Avoid Collisions:**
To avoid bucket collisions build an array of size M(number of buckets) where for each of the *mth* index of array build an linked list of the key-value pairs whose keys hash to that index (bucket index). 

The better idea is to choose M sufficienty large so that the lists are sufficienty short.

*Search* can be done in two-step process:
1. Hash(key) to find the bucket index. 
2. Linear search through the list for the key.  
3. If key is in the linked list, return the associated value; otherwise return null;

*Insert* can be done in 2-step process:
1. Hash(key) to identify the bucket index.
2. Linear search through the list for the key.
3. If the key is in the linked list, replace the old value associated with key with new one; otherwisw create a new node with the new <key-value> pair and insert it at the beginning of the linked list.

![picture](hash-table.png)

*Depiction of how __hashmap__ works*

**API**

```java
	public class HashMapSeparateChaining<Key, Value>
		HashMapSeparateChaining()     // create a hash table with capacity = 888
		void put(Key key, Value val)    // insert key-value pair
		Value get(Key key)             //  fetch the value associated with key
```

**How to run the code**
1. Clone the repo.
2. Compile the program using command `javac -d . HashMapSeparateChaining.java`.
3. Compile the test program using command `javac -d . Tester.java`.
4. Execute the test program using command `java cassandratest.Tester`.

**Tests performed**

![picture](screenshot_1.png)

From the tests performed:

`hash(Raja) = 382`, `hash(Aajr) = 382`, `hash(Jaar) = 382` which may lead to collision. But the strategy applied in the program avoids the collisions with the help of Linked Lists.

