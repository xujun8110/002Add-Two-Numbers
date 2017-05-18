# 002Add-Two-Numbers
给两个链表：Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)
           Output: 7 -> 0 -> 8
第一道链表题，顺便复习一下链表知识
链表题目一般加一个表头dummyhead,和一个当前节点p
经验总结：想好思路在动手，没思路的话就按最简单的方法边想边写，否则会浪费很多时间debug。。

上代码：
public class Solution {
    public ListNode addTwoNumbers(ListNode l1, ListNode l2) {
        ListNode dummyHead = new ListNode(0);
        ListNode p = dummyHead, p1 = l1, p2 = l2;
        int carry = 0;
        
        while(p1 != null || p2 !=null) {
            int addNumber = 0;
            if(p1 != null) {
                addNumber += p1.val;
                p1 = p1.next;
            }
            
            if(p2 !=null) {
                addNumber += p2.val;
                p2 = p2.next;
            }
            
            int sum = addNumber + carry;
            p.next = new ListNode(sum % 10);
            carry = sum / 10;
            p = p.next;
        }
        
        //最后一个进位忘了，没有通过用例....
        if(carry > 0) {
            p.next = new ListNode(carry);
        }
        
        return dummyHead.next;
    }
}
