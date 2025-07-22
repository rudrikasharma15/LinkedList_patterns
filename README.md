 **comprehensive Linked List Patterns**



### **1. Traversal & Basic Operations**

**Concept:** Building, traversing, inserting, deleting.

**Template:**

```java
// Traversal
ListNode curr = head;
while(curr != null){
    // process curr.val
    curr = curr.next;
}

// Insert at head
ListNode node = new ListNode(val);
node.next = head;
head = node;

// Delete by value
ListNode dummy = new ListNode(0);
dummy.next = head;
ListNode prev = dummy;
while(prev.next != null){
    if(prev.next.val == target) prev.next = prev.next.next;
    else prev = prev.next;
}
return dummy.next;
```

**Practice:**

* Implement singly, doubly, circular LL.
* Print, insert, delete.

---

### **2. Reversal Variations**

**Concept:** Most-used interview base. Handle full list, sublists, groups.

**Template (Iterative):**

```java
ListNode prev = null, curr = head;
while(curr != null){
    ListNode next = curr.next;
    curr.next = prev;
    prev = curr;
    curr = next;
}
return prev;
```

**Sublist / k-group:** Use dummy + reverse helper for \[m,n] or every k nodes.

**Practice:**

* Reverse full list (iterative/recursive)
* Reverse in groups of k
* Reverse sublist (m, n)

---

### **3. Fast & Slow Pointers**

**Concept:** Detect cycles, find middle, palindrome.

**Template:**

```java
// Find middle
ListNode slow = head, fast = head;
while(fast != null && fast.next != null){
    slow = slow.next;
    fast = fast.next.next;
}
// slow = middle

// Detect cycle
while(fast != null && fast.next != null){
    slow = slow.next;
    fast = fast.next.next;
    if(slow == fast) return true;
}
```

**Practice:**

* Detect cycle & find cycle start.
* Find middle node (even/odd).
* Palindrome check (reverse second half).

---

### **4. Merge & Sorting**

**Concept:** Combining and sorting LL efficiently.

**Template (Merge Two):**

```java
ListNode dummy = new ListNode(0), tail = dummy;
while(l1 != null && l2 != null){
    if(l1.val < l2.val){ tail.next = l1; l1 = l1.next; }
    else { tail.next = l2; l2 = l2.next; }
    tail = tail.next;
}
tail.next = (l1 != null) ? l1 : l2;
return dummy.next;
```

**Practice:**

* Merge 2 or K sorted lists (heap).
* Sort list (merge sort).

---

### **5. Two-Pointer Tricks**

**Concept:** Gap method (nth from end, intersections).

**Template (Nth from end):**

```java
ListNode fast = head, slow = head;
for(int i=0;i<n;i++) fast = fast.next;
while(fast != null){
    fast = fast.next;
    slow = slow.next;
}
// slow is (len-n)th node
```

**Practice:**

* Remove nth node.
* Find intersection.
* Add numbers (forward/backward).

---

### **6. Dummy Node Pattern**

**Concept:** Simplifies edge-case handling (head changes).

**Template:**

```java
ListNode dummy = new ListNode(0);
dummy.next = head;
ListNode prev = dummy;
while(head != null){
    if(head.val == target) prev.next = head.next;
    else prev = head;
    head = head.next;
}
return dummy.next;
```

**Practice:**

* Remove duplicates (sorted).
* Swap nodes in pairs.
* Odd-even list.

---

### **7. Backtracking + LL**

**Concept:** Rare (used for generating permutations/paths).

**Template:**
Use recursion to build paths, revert state (like DFS).

**Practice:**

* Generate permutations stored as LL.
* Recursively reverse with paths.

---

### **8. Multilevel & Advanced**

**Concept:** Non-standard LL (random pointers, flattening).

**Template (Clone with map):**

```java
Map<Node, Node> map = new HashMap<>();
Node curr = head;
while(curr != null){
    map.put(curr, new Node(curr.val));
    curr = curr.next;
}
curr = head;
while(curr != null){
    map.get(curr).next = map.get(curr.next);
    map.get(curr).random = map.get(curr.random);
    curr = curr.next;
}
return map.get(head);
```

**Practice:**

* Flatten multilevel DLL.
* Clone with random pointers.

---

### **9. Stack + LL Combo**

**Concept:** Handle next-greater, reverse order sums.

**Template:**

```java
Stack<Integer> st = new Stack<>();
int[] res = new int[size];
for(int i=size-1;i>=0;i--){
    while(!st.isEmpty() && st.peek() <= arr[i]) st.pop();
    res[i] = st.isEmpty()?0:st.peek();
    st.push(arr[i]);
}
```

**Practice:**

* Next greater node.
* Remove nodes greater than right.

---

### **10. Advanced (Hard Cases)**

**Concept:** Combines multiple patterns.

* Reverse K-group (dummy + reversal + counting).
* LRU Cache (DLL + HashMap).
* Rotate List (find new head using length).

