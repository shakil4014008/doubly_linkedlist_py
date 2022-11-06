# doubly_linkedlist_py

````py
class Node:
  def __init__(self, value):
    self.data = value
    self.prev = None
    self.next = None

class DoublyLinkedList:
  def __init__(self):
    self.head = None
    self.tail = None

  def insert_at_beginning(self, value):
    newNode = Node(value)
    if self.head is None:
      self.head = self.tail = newNode
      return
    newNode.next = self.head
    self.head.prev = newNode
    self.head = newNode

  def insert_at_end(self, value):
    newNode = Node(value)
    if self.head is None:
      self.head = self.tail = newNode
      return
    self.tail.next = newNode
    newNode.prev = self.tail
    self.tail = newNode

  def insert_in_middle(self, insertAfter, value):
    if self.head is None:
      return
    newNode = Node(value)
    current_node = self.head
    while current_node!=None and current_node.data != insertAfter:
      current_node = current_node.next
    if current_node!=None:
      tmp = current_node.next
      current_node.next = newNode
      newNode.prev = current_node
      newNode.next = tmp
      tmp.prev = newNode
    
  def delete_from_beginning(self):
    if self.head is None:
      return
    tmp = self.head.next
    self.head.next = None
    tmp.prev = None
    self.head = tmp

  def delete_from_end(self):
    if self.head is None:
      return
    if self.head.next is None:
      self.head = self.tail = None
      return
    tmp = self.tail.prev
    tmp.next = None
    self.tail.prev = None
    self.tail = tmp

  def delete_from_middle(self, value):
    if self.head is None:
      return
    if self.head.data == value:
      self.delete_from_beginning()
      return
    if self.tail.data == value:
      self.delete_from_end()
      return
    current_node = self.head
    while current_node!=None and current_node.data != value:
      current_node = current_node.next
    if current_node!=None:
      prev_node, next_node = current_node.prev, current_node.next
      prev_node.next = next_node
      next_node.prev = prev_node
      current_node.next = current_node.prev = None
    
  def print(self):
    current_node = self.head
    flag = 0
    while current_node:
      print('<->'*flag + str(current_node.data), end = "")
      flag = 1
      current_node = current_node.next
    print()


dll = DoublyLinkedList()
dll.print()
dll.insert_at_beginning(1)
dll.print()
dll.insert_at_end(2)
dll.print()
dll.insert_at_end(3)
dll.print()
dll.insert_at_end(4)
dll.print()

dll.insert_at_beginning(5)
dll.print()
dll.insert_at_end(6)
dll.print()
dll.insert_in_middle(3,7)
dll.print()

dll.delete_from_beginning()
dll.print()

dll.delete_from_end()
dll.print()

dll.delete_from_middle(3)
dll.print()

dll.delete_from_middle(1)
dll.print()

dll.delete_from_middle(4)
dll.print()
````
