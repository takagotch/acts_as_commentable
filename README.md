### acts_as_commentable
---
https://github.com/jackdempsey/acts_as_commentable


```
gem 'acts_as_commentable'
rails g comment
rake db:migrate
```

```ruby
class Post < ActiveRecord::Base
  acts_as_commentable
end

commentable = Post.create
comment = commentable.comments.create
comment.title = "First comment."
comment.comment = "This is the first comment."
comment.save
commentable = Post.find(1)
comments = commentable.comments.recent.limit(10).all

class Todo < ActiveRecord::Base
  acts_as_commentable :public, :private
end

public_comments = Todo.find(1).public_comments
private_comments = Todo.find(1).private_comments

class Todo < ActiveRecord::Base
  acts_as_commentable :public, :private, { class_name: 'MyComment' }
end

```

