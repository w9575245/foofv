# foofv
import { useState } from "react";
import { Card, CardContent } from "@/components/ui/card";
import { Button } from "@/components/ui/button";
import { Input } from "@/components/ui/input";

export default function FoodApp() {
  const [foods, setFoods] = useState(["Pizza", "Burger", "Sushi"]);
  const [newFood, setNewFood] = useState("");

  const addFood = () => {
    if (newFood.trim()) {
      setFoods([...foods, newFood.trim()]);
      setNewFood("");
    }
  };

  return (
    <div className="p-6 max-w-md mx-auto space-y-4">
      <h1 className="text-xl font-bold">Food List</h1>
      <div className="flex gap-2">
        <Input
          value={newFood}
          onChange={(e) => setNewFood(e.target.value)}
          placeholder="Enter food name"
        />
        <Button onClick={addFood}>Add</Button>
      </div>
      <div className="space-y-2">
        {foods.map((food, index) => (
          <Card key={index}>
            <CardContent className="p-2 text-center">{food}</CardContent>
          </Card>
        ))}
      </div>
    </div>
  );
}
